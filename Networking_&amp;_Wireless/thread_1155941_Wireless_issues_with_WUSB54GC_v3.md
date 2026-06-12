---
title: "Wireless issues with WUSB54GC v3"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by radixor on 2009-05-11
[SIZE="6"][COLOR=Black][SEE BELOW FOR RESOLUTION TO GETTING THIS TO WORK][/COLOR][/SIZE]

Hi, I just upgraded my ubuntu from 7.04 -> 9.04 after a short hiatus from Ubuntu to SuSE10. I have purchased yesterday a LinkSys WUSB54GC wireless adapter and plugged it into my usb port. It did not work. However, lsusb showed that my linksys card was recognized. 

LinkSys cards use the rtxxxxx chips, so I wanted to see what version of rt I should have. I checked the cd and found that there's an adapter called rt2870.inf, so I figured that I am rt2870. (Can someone here confirm this?) I decided to follow the steps here: [http://ubuntuforums.org/showthread.php?t=960642](http://ubuntuforums.org/showthread.php?t=960642)

I used this .tar.gz file:
04/24/2009    2.1.1.0
RT2870USB(RT2870/RT2770)  [http://www.ralinktech.com.tw/data/drivers/2009_0424_RT2870_Linux_STA_V2.1.1.0.tgz](http://www.ralinktech.com.tw/data/drivers/2009_0424_RT2870_Linux_STA_V2.1.1.0.tgz)

I built the driver, did an insmod st2870sta.ko, then i put rt2870sta in /etc/modules

Somewhere along the steps in that tutorial, my light turned green! Which is a huge step towards connectivity..

When I do a iwconfig,  I see my adapter, as well as when I do a ifconfig.
When I did a /etc/init.d/networking restart, I see that there is no dhcp server, as we're making DHCPREQUESTs, but I receive no DHCPOFFERS. I can not see my wireless network, nor can I see any of my neighbors. 

I have pretty much lost a good 10+ hours on this, any ideas on what do? 
Thanks!

---

### Post by radixor on 2009-05-12
**[COLOR="Red"]> [SIZE="6"]NEW LINK TO DOWNLOAD WUSB54GC v3 DRIVERS (1.4.0.0) [http://bit.ly/4pPyzx](http://bit.ly/4pPyzx)[/SIZE] [/COLOR]**

**[COLOR="Black"][SIZE="6"]Please see above link for working file[/SIZE][/COLOR]**

Guys, here's a step-by-step process on how to resolve this issue on Ubuntu 9.04:

**The drivers that work with WUSB54GC v3 _ARE NOT_ THE 2.1.1.0 on the RALINK site.** 
They are the [http://www.ralink.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2](http://www.ralink.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2)

BEFORE EXECUTING ANY OF THESE STEPS, PLEASE DO A ```
 sudo -i 
```

Step 1.
```
 wget http://www.ralink.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2 
```

Step 2.
```
 tar xjf 2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2 
```

Step 3.
```
 cd 2008_0925_RT2870_Linux_STA_v1.4.0.0 
```

Step 4.
replace the file located in [FONT="Courier New"]include/rt2870.h[/FONT] with [FONT="Courier New"]rt2870.h[/FONT] from the attached [FONT="Courier New"]rt2870.h.tar.gz[/FONT]

Step 5.
Execute
```
 perl -p -i.old -e 's/(HAS*WPA*SUPPLICANT*=)n/{$1}y/g' os/linux/config.mk 
```

Step 6.
```
 make && make install 
```

Step 7.
Make sure that [FONT="Courier New"]/lib/modules/`uname -r`/updates/[/FONT] exists! If this directory does not exist, then create it.

After you've ensured that it does exist, then run:
```
 cp -p /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2870sta.ko /lib/modules/`uname -r`/updates/ 
```

Step 8.
```
 depmod -a 
```

Step 9.
```
 gedit /etc/Wireless/RT2870STA/RT2870STA.dat 
```
Change the following (obviously depends on your connection):
[INDENT][LIST]
SSID=<YOUR-SSID>
Channel=<YOUR-CHANNEL>
AuthMode=WPA
EncrypType=TKIP
WPAPSK=<YOUR-PASS-KEY-HERE>
[/LIST][/INDENT]
AuthMode, EncrypType can be any of the values you see below.
For WEP, you would have AuthMode=WEPAUTO and EncrypType=WEP
For WPA, you would have AuthMode=WPA and EncrypType=TKIP (** **your values here may differ** **)
```

@> AuthMode=value
        value
                OPEN        For open system 
                SHARED      For shared key system   
                WEPAUTO     Auto switch between OPEN and SHARED
                WPAPSK      For WPA pre-shared key  (Infra)
                WPA2PSK     For WPA2 pre-shared key (Infra)
                WPANONE     For WPA pre-shared key  (Adhoc)
                WPA         Use WPA-Supplicant
                WPA2        Use WPA-Supplicant

@> EncrypType=value
        value
                NONE        For AuthMode=OPEN                    
                WEP         For AuthMode=OPEN or AuthMode=SHARED 
                TKIP        For AuthMode=WPAPSK or WPA2PSK                    
                AES         For AuthMode=WPAPSK or WPA2PSK                     

```                

Step 10.
```
 echo "alias ra0 rt2870sta" >> /etc/modules 
```

Step 11.
```
 
echo "ifconfig ra0 inet up" >> /etc/init.d/rc.local

```

Step 12.
Reboot

Step 13.
If you're not connected to the internet by now, there is **_ONE_** more step to take but you have **_TWO CHOICES_**:

Step 13a.
Something that I learned that activated my network-manager was this:
```
sudo vi /etc/NetworkManager/nm-system-settings.conf
```
Change "managed=false" to "managed=true"
```
sudo killall nm-system-settings
```

This should pop up and you should see all your wireless networks!

If this works, SKIP STEP 13B.
If you want to use the command-line, use the below step.

Step 13b.
Using wpa_supplicant to connect!
Read this great tutorial/walk-through here: 
[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)


-------------------------------------------------------------

PLEASE NOTE THAT THE WIRELESS ADAPTER DOES NOT BLINK OR LIGHT UP GREEN BUT IT STILL WORKS. TO TEST THIS YOU CAN TYPE ```
iwlist ra0 scan
``` and it will show all the wireless networks nearby.


Please leave some feedback or your comments. 

Thanks,
radixor.

P.S. I will write a small python script to automate this ordeal...

---

### Post by smacattack on 2009-05-12
Sorry for the noob question, but how can I find my SSID, channel, and all that? I tried the rest of the instructions there to no avail so I'm hoping that's all I need to fix. Thanks so much for the help...

---

### Post by radixor on 2009-05-12
> **smacattack said:**
> Sorry for the noob question, but how can I find my SSID, channel, and all that? I tried the rest of the instructions there to no avail so I'm hoping that's all I need to fix. Thanks so much for the help...

No problems! Your SSID, channels, etc are all configured on your wireless router. 

However, I can only answer based on your answers of this question:

Is your router already setup and running? 
If yes, then type in: ```
 iwlist <%DEVICE%> scan 
``` where your <%DEVICE%> is your device port (usually ra0), e.g. ( ```
 iwlist ra0 scan 
``` )

If no, then your wireless will usually have defaults, which you will find easily again by typing in ```
 iwlist ra0 scan 
```

---

### Post by gordonjay on 2009-05-12
i googled this same problem 2 days ago, but didn't find anything that solved it. thanks!!!

did v3 of this device just come out or something? i am total MS-fed n00b :(

---

### Post by radixor on 2009-05-12
> **gordonjay said:**
> i googled this same problem 2 days ago, but didn't find anything that solved it. thanks!!!

did v3 of this device just come out or something? i am total MS-fed n00b :(

Hi, I have no idea if this came out recently, from what I can tell, the rt2870 2.1.1.0 drivers which were dated 04/14/2009 from ralink.com's website did NOT have the usb serial in the header files! Which means that it might've come out within the last few months. 

I checked LinkSys, v3 is definitely the newest version. However, the 1.4.4.0 drivers WORK ABSOLUTELY PERFECTLY. I am hoping for a better driver to emerge soon from RaLink (one that makes the green light work). I might have to even read the source code to see what the problems would be and compile my own driver.

Will keep you guys posted.

---

### Post by smacattack on 2009-05-12
radixor: I'll check the router through another computer on the network. I haven't got anything set up on this computer so I can't scan anything from here. I'm hopeful this will work for me so thanks so much!

gordonjay: ya v3 just came out recently

---

### Post by gordonjay on 2009-05-12
so i made it to step 7: cp -p /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2870sta.ko /lib/modules/`name -r`/updates

but i got this error: -bash: name: command not found

past experiences with errors in setting up things in Linux persuade me to stay where i am at. i Googled "-bash: name: command not found"+Ubuntu+9.04 but only got 2 results, both of which were technical enough to make my head explode.

---

### Post by radixor on 2009-05-12
> **gordonjay said:**
> so i made it to step 7: cp -p /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2870sta.ko /lib/modules/`name -r`/updates

but i got this error: -bash: name: command not found

past experiences with errors in setting up things in Linux persuade me to stay where i am at. i Googled "-bash: name: command not found"+Ubuntu+9.04 but only got 2 results, both of which were technical enough to make my head explode.

Sorry! Looks like I had a typo!!

use this:

```

cp -p /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2870sta.ko /lib/modules/`**uname** -r`/updates


```

---

### Post by gordonjay on 2009-05-12
you rule!

---

### Post by smacattack on 2009-05-13
so I got the SSID info and that from my router did the whole process over on a fresh install of jaunty with no luck.

I have yet to do that last step as it scared me upon first look but it doesn't look too bad now so i'll give it a whirl

the only other thing I can think of is that my router security was setup as WEP instead of WPA, so I guess I should switch it and try again? (since the instructions talk about WPA)

man, I really wish this adapter would 'just work' like its predecessors (prior to version 3)

---

### Post by radixor on 2009-05-13
> **smacattack said:**
> so I got the SSID info and that from my router did the whole process over on a fresh install of jaunty with no luck.

I have yet to do that last step as it scared me upon first look but it doesn't look too bad now so i'll give it a whirl

the only other thing I can think of is that my router security was setup as WEP instead of WPA, so I guess I should switch it and try again? (since the instructions talk about WPA)

man, I really wish this adapter would 'just work' like its predecessors (prior to version 3)

Can you post me your:

```
 iwlist ra0 scan 
```

```
 lshw -class network 
```

Yes, if you have WEP, you will need to change it to WEP.
Something that I learned that activated my network-manager was this:

```
sudo vi /etc/NetworkManager/nm-system-settings.conf
```

Change "managed=false" to "managed=true"

```
sudo killall nm-system-settings
```


See if something pops up.
Hope this helps, 

Radixor

---

### Post by smacattack on 2009-05-14
Here is the output of  "iwlist ra0 scan": 

ra0       Interface doesn't support scanning.


and here is the output of "lshw -class network":

 *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 02
       serial: 00:11:11:1f:a9:8e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 4e:bb:59:d4:d4:2e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes




Thanks so much for any insights...I'm going try another fresh install tomorrow and go through all the steps again and cross my fingers...

---

### Post by radixor on 2009-05-14
> **smacattack said:**
> Here is the output of  "iwlist ra0 scan": 

ra0       Interface doesn't support scanning.


and here is the output of "lshw -class network":

 *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 02
       serial: 00:11:11:1f:a9:8e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 4e:bb:59:d4:d4:2e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes




Thanks so much for any insights...I'm going try another fresh install tomorrow and go through all the steps again and cross my fingers...

Looks like your driver is actually not installed, what is the model number of your LinkSys adapter? 

Can you please do an:
```
 lsmod 
```

and then please execute this and paste the results:

```
 if [[ `lsmod | grep rt2870 | wc -l` -eq 1 ]]; then modinfo rt2870sta; else echo "couldn't find rt2870"; fi 
```

also please execute this (make sure the adapter is plugged in the usb):

```
 lsusb 
```

Paste that here for me. 

Thanks!
Radixor

---

### Post by MorganTheDark on 2009-05-15
> **smacattack said:**
> Here is the output of  "iwlist ra0 scan": 

ra0       Interface doesn't support scanning.



I had this problem too. I fixed it by going to Network in the System/Administration menu and disabling roaming on the wireless connection. Not sure how to do that through the command line or what exactly it does, but it fixed my problem.

---

### Post by smacattack on 2009-05-15
Radixor you are my hero!

I did a fresh install and followed your instructions again and the adapter works! (I'm not sure what I did differently except I made sure to install build-essential beforehand this time so I don't know if that was it).

The 2 wireless networks in my house show up now, but I'm not able to connect to them for some reason (one green orb things lights up in the systray but not the other...it just keeps trying and trying).

I have a feeling my problems now are just due to the funny wireless setup in my house...so I'll have to work on that.

Either way, at least it works now, thanks so much for the adapter instructions man, and for your time, you are a saviour!

---

### Post by Laundry on 2009-05-15
I'm having the same issue as smacattack it seems.  This is what I'm getting when I do those commands: [http://pastebin.com/m1714ca81](http://pastebin.com/m1714ca81) .  This is off of a fresh install of 9.04.  I would do what MorganTheDark is saying, but there is no Network option, unless he means Network Tools, but there is no option there (at least for me) to disable roaming.

---

### Post by smacattack on 2009-05-15
> **Laundry said:**
> I'm having the same issue as smacattack it seems.  This is what I'm getting when I do those commands: [http://pastebin.com/m1714ca81](http://pastebin.com/m1714ca81) .  This is off of a fresh install of 9.04.  I would do what MorganTheDark is saying, but there is no Network option, unless he means Network Tools, but there is no option there (at least for me) to disable roaming.

radixor is the expert so I'm sure he can help you more but just from my experience, I know for certain that editing the RT2870STA.dat file to the proper SSID and channel were key in having it eventually work for me (after I got the adapter to work I edited the .dat file back to what it was just to test and the adapter no longer worked).

Also I did a 'sudo apt-get install build-essential' before beginning radixors steps, as well as substituting the typo fix for step 7 as seen on the bottom of the first page of this thread. (also I did 'depmod -a' in step 8 instead of 'depmod**e** -a' just cause it was giving error messages)

---

### Post by Laundry on 2009-05-16
I am pretty sure I did all of those things, except for installing build-essential because this computer is not connected to the internet.  Is it possible for me to do an offline install from the CD?

---

### Post by jimbob on 2009-05-16
I was able to make this device work (green LED and all) but only using an open router configuration.  However I need WPA2 so it is, for the present time at least, useless to me. 

By the way, mine has one of the newer chips in it, the rt3070, device ID={0x1737,0x0077}.

If anyone has been successful in getting it to work with wpa2 please share your secrets on this thread.

---

### Post by Laundry on 2009-05-16
Okay, I reinstalled Jaunty and got it to install.  The card detects my wireless network, but refuses to connect to it.  I have no security on the network, so I have no idea what would be causing it to fail.

---

### Post by smacattack on 2009-05-16
> **Laundry said:**
> Okay, I reinstalled Jaunty and got it to install.  The card detects my wireless network, but refuses to connect to it.  I have no security on the network, so I have no idea what would be causing it to fail.

Looks like we're in the same boat man! There's 2 wireless networks in my house, 1 with security, 1 without. They both show up in the network manager but I can't connect to either. 

I guess you don't need to know anymore, but for future reference you can install build-essential offline by using the Ubuntu CD just type the following in a terminal with the CD in the drive:

sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential

---

### Post by hmmdar on 2009-05-16
try this
[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html/comment-page-1](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html/comment-page-1)

I was able to connect to an open connection using these settings.  My network manager still shows as no connection, but its a start


/editx2
Apologize i still have yet to get WPA to work with this adapter when i thought it was working, my router was still set in open mode :-/

// Edit
Just tried this out with WPA2, the instructions work great for the rt2870   wireless nic.  for the rt/ra devices these instructions work, but there is still the issue of Firefox not knowing the connection is actually alive and will start in off line mode
```

sudo ifconfig [interface] down
sudo dhclient -r [interface]
sudo ifconfig [interface] up
sudo iwconfig [inteface] essid “ESSID_IN_QUOTES”
sudo iwpriv [interface] set AuthMode=WPAPSK
sudo iwpriv [interface] set EncrypType=TKIP
sudo iwpriv [interface] set WPAPSK=”YOUR_WPA_PSK_KEY”
sudo dhclient [interface]

```and note to get "YOUR_WPA_PSK_KEY" use
```

wpa_passphrase ESSID_IN_QUOTES PSK_PASSWORD

```where PSK_PASSWORD is the password you use to generate the WPAPSK key

---

### Post by smacattack on 2009-05-16
jimbob, my adapter seems to have a new (rt3070) chipset (i just did lsusb and it shows 1737:0077, that's what that means right?). 

My adapter recognizes wireless connections using radixors instructions with rt2870 but I can't seem to connect.

What method did you use to get it working?

---

### Post by jimbob on 2009-05-17
I'm copying this from a PM between me and Dragonkeeper about a month ago.
You can read my original thread (if you haven't already) at [http://ubuntuforums.org/showthread.php?t=1089893&highlight=rt3070](http://ubuntuforums.org/showthread.php?t=1089893&highlight=rt3070)

Here is what else I did: (most of this from README_STA in main directory)

[I][COLOR="RoyalBlue"]1) in ...os/linux/usb_main_dev.c added line {USB_DEVICE(0x1737,0x0077)} /* Linksys WUSB54GC */
2) in ...os/linux/config.mk set 2 lines referring to WPA_SUPPLICANT to "y".
3) created /etc/sysconfig/network-scripts/ifcfg-ra0 and added lines;
      DEVICE='ra0'
      ONBOOT='yes'
      BOOTPROTO='dhcp'
4) added line in /etc/modules.conf  => alias ra0 rt3070sta
5) created (modified) the supplied RT3070STA.dat for my own SSID and WPA2-PSK; then did make install to get it inserted in /etc/Wireless/RT3070.  NOTE!!  You will find that what is created is named /etc/Wireless/RT3070STA/RT3070STA.dat.
You must rename this to /etc/Wireless/RT2870STA/RT2870STA.dat because this is what the system ends up looking for.[/COLOR][/I]
  
I gave up spending more time on it for now as I am using a D-Link DWL-G122 which works OOTB with Jaunty that was purchased for $14.99 with free shipping on E-Bay.
Good luck with yours.

---

### Post by smacattack on 2009-05-17
Awesome jimbob I'll give that a whirl today, thanks so much!

---

### Post by bbelden on 2009-05-22
I'm not sure if I'm posting this in the right place but my wusb54gc adapter does not even show up in Ubuntu 9.04. My adapter does not say if it is version 3 or not but it does have a date of 12/2006 so I'm guessing it is a version prior to 3. I have read probably a hundred posts on this adapter and all of them have stated that the adapter at least shows up in "lsusb". Anyone have an idea where I start on this? There are so many posts on so many versions of this adapter, I don't know where to start because I can't get Jaunty to recognize it to get the chipset.

Thanks in advance for any help.

---

### Post by jimbob on 2009-05-23
Just some random thoughts here.

  If you are using a cable, plug it in directly to the USB port.
It should definitely show up when plugged in with the lsusb command.
Bring up the system logs from the main menu and select syslog and scroll to the very bottom.  Then plug it in and watch the log.  Do you see anything at all?  Does it even recognize that anything has been plugged?

As a last desperate resort does it work in Windows?  Does Windows see it at all when it is plugged in?

---

### Post by bbelden on 2009-05-24
Thanks for your help JimBob.

Yes the adapter works with XP. I have been using it for about two years under windows. I could never get this adapter to work with any Ubuntu distro starting with Ubuntu 7. 

I checked the syslog as I plugged and unplugged the adapter and...nothing--it does not show up at all. Do I have to have the driver for this adapter loaded before Ubuntu will notice it? I need to mention again that this adapter is a version 1.
thanks

---

### Post by jimbob on 2009-05-24
If you don't see ANY evidence (even a one-liner about a USB device being plugged) in the system log I don't think you have a prayer.
I don't understand that at all - especially if it works in ex pee.

Take a look at this link to see if you can find anything about a Version 1 - I could not.  Is it definitely a WUSB54GC v1 made by Linksys?

[http://linux-wless.passys.nl/query_alles.php](http://linux-wless.passys.nl/query_alles.php)

---

### Post by baw4h on 2009-05-26
Has anyone tried using the driver RT3070USB released on 5/20 v 2.1.1.0 on Ralink's website [http://web.ralinktech.com/ralink/Home/Support/Linux.html](http://web.ralinktech.com/ralink/Home/Support/Linux.html)

---

### Post by jimbob on 2009-05-26
No - thanks for pointing that out.  I might give it a whirl later today.

EDIT: I just had a look at that new driver package and it is pretty much empty!  The earlier ones, particularly 4/24/09 had ~ 2.9MB while this one has 67Kb??  I think Ralink goofed on this.  There are the customary 6 folders after unpacking but they are all empty!
  Unless I'm missing something, this is a big goof-up ...

---

### Post by baw4h on 2009-05-27
I'm having the same trouble as smacattack, > *"My adapter recognizes wireless connections using radixors instructions with rt2870 but I can't seem to connect."*

I emailed support, awaiting response.  But, I missed this last time:  
[LEFT][RT2870USB(RT2870/RT2770)]("http://www.ralinktech.com.tw/data/drivers/2009_0521_RT2870_Linux_STA_V2.1.2.0.tgz")[/LEFT]
05/21/2009
v2.1.2.0
That might be the right driver.

[http://web.ralinktech.com/ralink/Home/Support/Linux.html](http://web.ralinktech.com/ralink/Home/Support/Linux.html)
Release Notes
[V2.1.2.0]
1. Short GI sampling improvement.
2. Support Linux Kernel 2.6.29 - Jaunty's kernel
Hopefully this will solve it.  I need help with making it, though.

---

### Post by jimbob on 2009-05-27
Thanks.  At least this one unpacks properly into ~ 3.0Mb

I'll have a look at it this afternoon.

---

### Post by memspyder on 2009-05-27
Thanks Radixor u are the man, just when i was going to downgrade my wusb54gc to ver 1.
:KS:KS:KS:KS:KS
[B]
[/B]

[B]
[/B]

---

### Post by radixor on 2009-05-29
> **smacattack said:**
> Awesome jimbob I'll give that a whirl today, thanks so much!

Are you still having trouble? Sorry, I just moved and got my stuff setup again.

---

### Post by radixor on 2009-05-29
> **memspyder said:**
> Thanks Radixor u are the man, just when i was going to downgrade my wusb54gc to ver 1.
:KS:KS:KS:KS:KS
[B]
[/B]

[B]
[/B]

Glad you got it working!

---

### Post by radixor on 2009-05-29
> **baw4h said:**
> Has anyone tried using the driver RT3070USB released on 5/20 v 2.1.1.0 on Ralink's website [http://web.ralinktech.com/ralink/Home/Support/Linux.html](http://web.ralinktech.com/ralink/Home/Support/Linux.html)

I'll go ahead and try to install this on the weekend. I'll write up a list of my instructions

---

### Post by Beyond014 on 2009-06-04
Help!! I am a newbie.

I am stuck at Step 5.

When I type in the command, I got "Substitution replacement not terminated at -e line 1".

How do I solve this problem??

Thanks in advance.

---

### Post by radixor on 2009-06-04
> **Beyond014 said:**
> Help!! I am a newbie.

I am stuck at Step 5.

When I type in the command, I got "Substitution replacement not terminated at -e line 1".

How do I solve this problem??

Thanks in advance.

You copied the command incorrectly. perl is complaining that you did not end the quote post the -e expression.

```
perl -p -i.old -e 's/(HAS*WPA*SUPPLICANT*=)y/{$1}n/g' os/linux/config.mk
```

---

### Post by jtx0 on 2009-06-05
Thanks radixor for the 1.4 driver instructions they worked to get the adapter up and running.  I am having a similar problem to most as I can see all the networks but cannot connect to any (unsecure, WEP or WPA2).  Anyone learn anything new about this issue?

Ubuntu 9.04 on an AMD Phenom II 810 with 4 GB DDR3

---

### Post by radixor on 2009-06-05
jtx0,

Are you using network manager applet or are you trying to use wpa_supplicant?

---

### Post by jtx0 on 2009-06-05
I tried both.  I probably need to try the wpa_supplicant again as I don't think I did the setup correctly.  I just finished loading the 2.1.2.0 drivers as well with the same result from Network Manager.  I'll try supplicant again.  Any other advice?  Are you running Jaunty with no issues?  Thanks again.

---

### Post by radixor on 2009-06-05
> **jtx0 said:**
> I tried both.  I probably need to try the wpa_supplicant again as I don't think I did the setup correctly.  I just finished loading the 2.1.2.0 drivers as well with the same result from Network Manager.  I'll try supplicant again.  Any other advice?  Are you running Jaunty with no issues?  Thanks again.

Can you confirm that you see all the networks from NETWORK MANAGER? This is very very important. 

Please try to connect to one of any networks, whether it's yours or another. Before you connect, please execute this command in another shell window:

```
tail /var/log/syslog
```

Look to see what it's saying as you're trying to connect. Is it just timing out?

FYI, I am running 9.04 perfectly fine with the steps I've done above.

---

### Post by jtx0 on 2009-06-05
I see several wireless networks.  My router is currently setup with WPA2 AES only (I tried TKIP and AES as well as WPA and WPA2).

```
@jasmin-ii:~$ tail /var/log/syslog
Jun  5 19:24:02 jasmin-ii NetworkManager: <info>  Activation (ra0/wireless): asking for new secrets 
Jun  5 19:24:02 jasmin-ii NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> disconnected 
Jun  5 19:24:04 jasmin-ii NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1539 (get_secrets_dialog_response_cb): canceled. 
Jun  5 19:24:04 jasmin-ii NetworkManager: <info>  (ra0): device state change: 6 -> 9 
Jun  5 19:24:04 jasmin-ii NetworkManager: <info>  Activation (ra0) failed for access point (JTNet) 
Jun  5 19:24:04 jasmin-ii NetworkManager: <info>  Marking connection 'Auto JTNet' invalid. 
Jun  5 19:24:04 jasmin-ii NetworkManager: <info>  Activation (ra0) failed. 
Jun  5 19:24:04 jasmin-ii NetworkManager: <info>  (ra0): device state change: 9 -> 3 
Jun  5 19:24:04 jasmin-ii NetworkManager: <info>  (ra0): deactivating device (reason: 0). 
Jun  5 19:24:04 jasmin-ii NetworkManager: <info>  Policy set 'Auto Ethernet' (eth0) as default for routing and DNS. 
```

The Network Manager tries to connect and asks for a network key.  It fails to connect and keeps asking for the key as it tries to reconnect.

---

### Post by radixor on 2009-06-05
> **jtx0 said:**
> I see several wireless networks.  My router is currently setup with WPA2 AES only (I tried TKIP and AES as well as WPA and WPA2).

```
@jasmin-ii:~$ tail /var/log/syslog
Jun  5 19:24:02 jasmin-ii NetworkManager: <info>  Activation (ra0/wireless): asking for new secrets 
Jun  5 19:24:02 jasmin-ii NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> disconnected 
Jun  5 19:24:04 jasmin-ii NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1539 (get_secrets_dialog_response_cb): canceled. 
Jun  5 19:24:04 jasmin-ii NetworkManager: <info>  (ra0): device state change: 6 -> 9 
Jun  5 19:24:04 jasmin-ii NetworkManager: <info>  Activation (ra0) failed for access point (JTNet) 
Jun  5 19:24:04 jasmin-ii NetworkManager: <info>  Marking connection 'Auto JTNet' invalid. 
Jun  5 19:24:04 jasmin-ii NetworkManager: <info>  Activation (ra0) failed. 
Jun  5 19:24:04 jasmin-ii NetworkManager: <info>  (ra0): device state change: 9 -> 3 
Jun  5 19:24:04 jasmin-ii NetworkManager: <info>  (ra0): deactivating device (reason: 0). 
Jun  5 19:24:04 jasmin-ii NetworkManager: <info>  Policy set 'Auto Ethernet' (eth0) as default for routing and DNS. 
```

The Network Manager tries to connect and asks for a network key.  It fails to connect and keeps asking for the key as it tries to reconnect.

OK, it looks like you're failing on authentication. If you're trying WPA2 and WPA, then make sure your changes are reflected in the rt2870sta.dat which you modified on step 9 of my original instructions.

Remember, and this is probably what's going on, *ANYTIME* a change is made to rt2870sta.dat **YOU MUST REBOOT!** There is no getting around that, you MUST reboot.


Just as a confirmation, can you also attempt to connect to a network again, but before you do that do a
```
dmesg
``` in another terminal and paste the results here

---

### Post by jtx0 on 2009-06-06
No joy.  I updated the .dat file and tried again with wpa_supplicant. Here's my dmesg output:

```
[ 9082.582877] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9102.343061] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[ 9103.501029] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[ 9103.501093] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9103.581046] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9118.516235] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 758
[ 9128.526381] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[ 9128.526445] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9128.569216] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9143.541595] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[ 9153.551729] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 949
[ 9153.551796] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9153.661390] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9162.341050] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[ 9168.566926] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[ 9178.577066] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[ 9178.577131] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9178.651434] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9193.592280] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 953
[ 9203.602444] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 942
[ 9203.602509] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9203.641105] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9222.343468] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1108
[ 9224.623798] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 949
[ 9224.623863] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9239.639024] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[ 9249.649180] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 942
[ 9249.649244] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9249.729072] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9264.664407] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 628
[ 9274.674561] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1108
[ 9274.674630] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9274.718992] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9282.339755] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 783
[ 9289.689792] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 433
[ 9299.699935] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 541
[ 9299.699998] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9299.811290] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9314.715158] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 787
[ 9324.725326] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 588
[ 9324.725389] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9324.802211] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9339.740552] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 671
[ 9339.740614] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9342.340118] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 671
[ 9354.755785] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 953
[ 9364.765970] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[ 9364.766032] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9364.848235] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9379.781204] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 433
[ 9389.789034] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[ 9389.789107] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9389.837647] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9402.343164] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 628
[ 9404.804282] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1108
[ 9404.804351] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9419.819529] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 953
[ 9429.829680] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 902
[ 9429.829745] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9429.882805] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9444.841875] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[ 9454.852026] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[ 9454.852093] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9454.881226] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9462.339045] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[ 9469.867238] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 787
[ 9479.877385] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[ 9479.877449] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9479.964524] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9494.892595] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 628
[ 9504.902734] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 736
[ 9504.902797] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9504.954443] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9519.917954] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1108
[ 9519.918020] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9522.340166] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1108
[ 9534.933195] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 841
[ 9544.943336] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 754
[ 9544.943398] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9545.000341] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9559.958553] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 386
[ 9569.968693] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1108
[ 9569.968761] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9570.093267] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9582.342671] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 552
[ 9584.983910] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[ 9584.983971] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9599.999131] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 599
[ 9610.009272] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 942
[ 9610.009335] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9610.039413] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9625.024492] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 599
[ 9635.034627] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 783
[ 9635.034692] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9635.127711] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9642.339459] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 942
[ 9650.049850] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 758
[ 9660.060009] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 476
[ 9660.060072] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9660.117631] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9675.075227] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[ 9685.085379] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[ 9685.085442] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9685.210055] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9700.100612] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1108
[ 9700.100677] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9702.340458] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1108
[ 9715.115837] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 628
[ 9725.125994] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 588
[ 9725.126055] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9725.158701] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9740.141223] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 599
[ 9750.151384] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 783
[ 9750.151448] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9750.250250] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9762.343123] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 433
[ 9765.166610] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[ 9765.166672] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9780.181804] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[ 9790.191929] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[ 9790.191990] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9790.290774] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9805.207126] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 552
[ 9815.217288] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 942
[ 9815.217356] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9815.281819] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9822.338981] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[ 9830.232495] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 787
[ 9840.242637] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 942
[ 9840.242701] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9840.274615] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9855.257840] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 321
[ 9865.267958] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1108
[ 9865.268023] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9865.363038] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9880.283168] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[ 9890.293313] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 588
[ 9890.293377] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9890.354958] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9905.308520] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 758
[ 9915.318664] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 942
[ 9915.318728] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9915.347879] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9930.332906] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 787
[ 9940.343057] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 541
[ 9940.343120] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9940.435677] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9942.340007] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 541
[ 9955.352752] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 758
[ 9965.362903] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 942
[ 9965.362967] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9965.425597] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[ 9980.378127] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 599
[ 9990.388300] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1108
[ 9990.388375] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[ 9990.419644] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10002.342878] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 588
[10005.403537] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[10005.403600] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10020.418754] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 758
[10030.428923] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[10030.428987] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10030.460915] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10045.444157] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 628
[10055.454311] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[10055.454377] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10055.553591] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10062.338736] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 783
[10070.469522] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 758
[10080.479694] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[10080.479757] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10080.544637] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10095.494918] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 433
[10105.504032] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1108
[10105.504098] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10105.636310] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10120.519240] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[10130.529388] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 949
[10130.529453] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10130.625730] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10145.544588] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[10155.554717] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 783
[10155.554780] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10155.615525] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10170.569910] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 953
[10180.580073] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 783
[10180.580137] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10180.610821] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10182.339963] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 783
[10195.595286] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 787
[10205.605442] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 783
[10205.605505] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10205.699119] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10220.620651] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 953
[10230.630806] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 743
[10230.630872] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10230.688040] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10242.343121] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[10245.646016] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[10245.646077] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10260.661231] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[10260.661320] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10260.696369] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10275.676472] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 433
[10285.686624] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[10285.686686] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10285.789293] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10300.701852] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 393
[10310.711991] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 588
[10310.712054] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10310.778961] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10325.727207] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[10335.737367] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 541
[10335.737429] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10335.778259] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10350.752582] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 758
[10360.762759] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[10360.762822] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10360.863306] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10362.339177] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[10375.777993] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 758
[10385.788170] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[10385.788232] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10385.851100] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10400.803357] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 599
[10410.813483] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 707
[10410.813548] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10410.845147] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10425.828674] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 433
[10435.838786] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[10435.838848] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10435.934196] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10450.853964] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[10460.864095] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 588
[10460.864159] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10460.926241] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10475.879290] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[10485.889420] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[10485.889483] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10500.904609] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[10510.914735] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[10510.914795] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10511.009835] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10525.929932] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 433
[10535.940065] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 635
[10535.940128] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10535.996631] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10542.337983] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 588
[10550.955266] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 433
[10560.965398] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[10560.965463] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10561.089054] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10575.980603] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 433
[10585.990736] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 588
[10585.990798] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10586.078223] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10601.005941] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[10611.016078] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 382
[10611.016145] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10611.069020] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10626.031277] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[10636.041413] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 635
[10636.041480] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10636.162068] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10651.056617] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[10661.066756] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[10661.066820] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10661.154739] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10662.339653] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[10676.081959] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 433
[10686.092091] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 635
[10686.092152] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10686.141533] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10701.107301] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 321
[10711.117436] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 270
[10711.117500] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10711.233082] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10726.132644] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 321
[10736.142771] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 642
[10736.142833] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10736.223252] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10751.157970] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[10761.168138] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 642
[10761.168203] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10761.214050] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10776.183360] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 480
[10786.193507] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[10786.193571] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10801.208724] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 433
[10811.218866] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[10811.218926] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10811.295516] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10826.234098] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 480
[10836.244253] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[10836.244318] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10836.285561] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10842.337880] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[10851.259475] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 433
[10861.269631] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 588
[10861.269698] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10861.378985] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10876.284860] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 599
[10886.295026] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 382
[10886.295088] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10886.367654] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10901.310258] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[10911.320425] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[10911.320490] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10911.358075] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10926.335694] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[10936.345880] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 754
[10936.345953] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10936.450002] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10951.361146] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 758
[10961.371334] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[10961.371401] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10961.440046] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[10962.338618] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[10976.386577] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 433
[10986.396744] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[10986.396806] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[10986.435215] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11001.411982] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 433
[11011.422122] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 541
[11011.422188] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11011.523263] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11026.437366] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 758
[11036.447554] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 588
[11036.447615] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11036.515683] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11051.462789] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[11061.469105] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[11061.469170] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11061.502228] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11076.484323] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[11086.494474] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[11086.494538] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11101.509652] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[11111.519771] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[11111.519832] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11111.586573] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11126.534956] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 552
[11136.545092] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[11136.545158] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11136.678121] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11142.337418] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 588
[11151.560294] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 599
[11161.570425] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 588
[11161.570491] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11161.668417] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11176.585620] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[11186.595752] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 588
[11186.595815] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11186.657087] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11201.610953] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[11211.621099] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[11211.621167] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11211.653383] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11226.636290] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[11236.646418] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[11236.646483] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11236.740181] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11251.661613] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 433
[11261.671736] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[11261.671801] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11261.732351] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11262.338461] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[11276.686934] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 599
[11286.697083] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[11286.697148] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11286.821649] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11301.712284] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 599
[11311.722422] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 588
[11311.722488] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11311.813070] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11326.737618] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[11336.747750] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 754
[11336.747814] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11336.801740] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11351.762941] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[11361.773080] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[11361.773143] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11361.802410] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11376.788286] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[11386.797092] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[11386.797156] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11401.812290] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 599
[11411.822427] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[11411.822486] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11411.874378] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11426.837627] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 433
[11436.847747] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[11436.847813] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11436.966802] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11442.337787] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[11451.862966] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 599
[11461.873111] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 588
[11461.873176] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11461.957847] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11476.888316] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 758
[11486.898470] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 588
[11486.898533] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11486.946892] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11501.913682] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[11511.923835] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[11511.923901] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11512.039192] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11526.939069] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 758
[11536.949208] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[11536.949272] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11537.029112] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11551.964419] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 758
[11561.974587] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[11561.974651] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11562.018907] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11562.338578] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[11576.989798] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[11586.999929] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 754
[11586.999992] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11587.111330] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11602.015142] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 433
[11612.025292] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 754
[11612.025365] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11612.101128] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11627.040519] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[11637.050677] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[11637.050743] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11637.091671] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11652.065892] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[11662.076052] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[11662.076118] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11662.183469] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11677.091280] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[11687.101433] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 754
[11687.101497] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11702.116653] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 321
[11712.126793] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[11712.126852] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11712.163434] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11727.142014] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 227
[11737.152169] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 588
[11737.152233] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11737.255983] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11742.336892] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[11752.167385] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[11762.177517] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 754
[11762.177583] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11762.245904] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11777.192712] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[11787.202844] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[11787.202908] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11787.237074] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11802.218062] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 758
[11812.228213] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[11812.228282] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11812.328249] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11827.243411] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[11837.253548] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 588
[11837.253612] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11837.318293] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11852.268750] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 433
[11862.278878] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[11862.278942] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11862.338335] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[11862.410591] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11877.294092] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 433
[11887.304224] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[11887.304286] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11887.400637] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11902.319428] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 758
[11912.329580] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 588
[11912.329645] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11912.390557] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11922.338135] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 754
[11927.343280] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 758
[11937.353431] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[11937.353495] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11937.385352] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11952.368628] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 386
[11962.378763] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 801
[11962.378826] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11962.473151] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11982.343332] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 476
[11983.400102] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 476
[11983.400162] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[11983.468819] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[11998.415306] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[12008.425456] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[12008.425517] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[12008.458614] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[12023.440674] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 592
[12033.450835] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[12033.450900] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[12033.551412] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[12042.341288] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 754
[12048.466070] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 758
[12058.476243] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 913
[12058.476309] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[12058.542583] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[12073.491468] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 433
[12083.500074] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 754
[12083.500150] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[12083.848259] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[12102.342751] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 801
[12104.521410] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 747
[12104.521482] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[12119.536635] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 393
[12129.546782] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 382
[12129.546854] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=9)
[12129.619220] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response

``` 
Here is the output from wpa_supplicant with the -dd flag:
```

Initializing interface 'ra0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=5):
     4a 54 4e 65 74                                    JTNet           
scan_ssid=1 (0x1)
proto: 0x3
key_mgmt: 0x2
pairwise: 0x10
group: 0x10
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='JTNet'
Initializing interface (2) 'ra0'
Interface ra0 set UP - waiting a second for the driver to complete initialization
SIOCGIWRANGE: WE(compiled)=22 WE(source)=14 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:23:69:72:43:18
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
Added interface ra0
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=5):
     4a 54 4e 65 74                                    JTNet           
Trying to get current scan results first without requesting a new scan to speed up initial association
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds
EAPOL: disable timer tick
Scan timeout - try to get results
Received 429 bytes of scan results (3 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1c:f0:55:c1:9b ssid='JTNet' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:1c:f0:55:c1:9b ssid='JTNet'
Trying to associate with 00:1c:f0:55:c1:9b (SSID='JTNet' freq=2452 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 2
WPA: clearing AP WPA IE
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RSN: Ignored PMKID candidate without preauth flag
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
Wireless event: cmd=0x8b04 len=16
Authentication with 00:1c:f0:55:c1:9b timed out.
Added BSSID 00:1c:f0:55:c1:9b into blacklist
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=5):
     4a 54 4e 65 74                                    JTNet           
Scan requested (ret=0) - scan timeout 5 seconds
Scan timeout - try to get results
Received 953 bytes of scan results (6 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:7e:2f:b7:29 ssid='Mordor' wpa_ie_len=28 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
1: 00:21:04:61:95:82 ssid='Darkesdomain' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:21:04:64:eb:b0 ssid='liisa' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:17:9a:20:e9:4c ssid='Drake' wpa_ie_len=22 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
4: 00:1c:10:b7:be:2c ssid='JKR' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
5: 00:11:95:08:06:0a ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1d:7e:2f:b7:29 ssid='Mordor' wpa_ie_len=28 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
1: 00:21:04:61:95:82 ssid='Darkesdomain' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:21:04:64:eb:b0 ssid='liisa' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:17:9a:20:e9:4c ssid='Drake' wpa_ie_len=22 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
4: 00:1c:10:b7:be:2c ssid='JKR' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
5: 00:11:95:08:06:0a ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No APs found - clear blacklist and try again
Removed BSSID 00:1c:f0:55:c1:9b from blacklist (clear)
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:7e:2f:b7:29 ssid='Mordor' wpa_ie_len=28 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
1: 00:21:04:61:95:82 ssid='Darkesdomain' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:21:04:64:eb:b0 ssid='liisa' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:17:9a:20:e9:4c ssid='Drake' wpa_ie_len=22 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
4: 00:1c:10:b7:be:2c ssid='JKR' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
5: 00:11:95:08:06:0a ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1d:7e:2f:b7:29 ssid='Mordor' wpa_ie_len=28 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
1: 00:21:04:61:95:82 ssid='Darkesdomain' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:21:04:64:eb:b0 ssid='liisa' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:17:9a:20:e9:4c ssid='Drake' wpa_ie_len=22 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
4: 00:1c:10:b7:be:2c ssid='JKR' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
5: 00:11:95:08:06:0a ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds
Scan timeout - try to get results
Received 707 bytes of scan results (5 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1c:f0:55:c1:9b ssid='JTNet' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:1c:f0:55:c1:9b ssid='JTNet'
Trying to associate with 00:1c:f0:55:c1:9b (SSID='JTNet' freq=2452 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 2
WPA: clearing AP WPA IE
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RSN: Ignored PMKID candidate without preauth flag
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
Wireless event: cmd=0x8b04 len=16
Authentication with 00:1c:f0:55:c1:9b timed out.
Added BSSID 00:1c:f0:55:c1:9b into blacklist
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=5):
     4a 54 4e 65 74                                    JTNet           
Scan requested (ret=0) - scan timeout 5 seconds
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface ra0
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Removed BSSID 00:1c:f0:55:c1:9b from blacklist (clear)
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6

```

Thanks again for the assistance.

---

### Post by baw4h on 2009-06-06
I've been receiving the same errors as jtxO
```
ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
```
 running 9.04 as well.  I turned off authentication and switched to mac authentication only on my router to pinpoint the problem.  same error, so authentication doesn't seem to be the problem.  I've tried installing driver v.2.1.2.0 using radixor's original instructions (except for perl substitution command and using the attached .h file) and that didn't work.  I'm still waiting for build instructions for 2.1.2.0

Here's a newbie question:  let's say I run an install but it doesn't work. How can I uninstall it if I use instructions similar to radixor's?

---

### Post by jtx0 on 2009-06-06
I have also tried no security with MAC filtering and no joy connecting.

To uninstall the driver you have to first disable the interface
```
sudo ifconfig ra0 down
```
then unload the module from the kernel
```
sudo rmmod rt2870sta
```
then go to the directory where you ran the make file from (2008_0925_RT2870_Linux_STA_v1.4.0.0) 
```
sudo make uninstall
```

I'm pretty sure that will completely remove it from you system but I'm a bit of a noob as well so stand by for corrections.

---

### Post by TOCie on 2009-06-07
> **radixor said:**
> Remember, and this is probably what's going on, *ANYTIME* a change is made to rt2870sta.dat **YOU MUST REBOOT!** There is no getting around that, you MUST reboot.

So, basically, with this chipset and driver, we are incapable of using Network Manager, wicd, etc to manage the connection at all?  

I think I'll be returning this WUSB54GC revision 3 to the store in favor of something else.  Thank you to everyone in this thread with instructions on getting this creature working, especially **hmmdar** on page 3, I had to manually poke the DHCP client to get things working.

---

### Post by jimbob on 2009-06-08
> I think I'll be returning this WUSB54GC revision 3 to the store in favor of something else

TOCie: Did you determine that you have the rt3070 chip?

IMHO Ralink has given little more than lip service to Linux support on this one.  In fact they have failed miserably.

---

### Post by jtx0 on 2009-06-09
I just did a clean install of Ubuntu 9.04 i386 32-bit on my machine to test.  Based on others' comments I didn't do any of the initial updates (105 of them).  I installed the 1.4.0 drivers based on the instructions in this thread and connected on WPA2 AES no problems through Network Manager.  Thanks for the good work by Radixor.  It would seem that one of those 105 updates impacts the WPA/WPA2 components of Network Manager and WPA Supplicant.  I'm not sure I will go through installing them one at a time to figure that out yet as I will probably celebrate a bit of WiFi connectivity for a while.

---

### Post by jtx0 on 2009-06-09
A quick update.  I was setting up the USB WiFi adapter for a friend and shortly after I updated the Firefox 3.0 updates (5 of them) I lost the connection and it went into cycling asking for the network key.  I am now running the adapter on my test setup (Ubuntu 9.04 not updated) over night to see if the connection is lost then I plan to apply one update at a time (except Firefox) to see if I kill the connection.  Hopefully, this will confirm that the Firefox 3.0 updates cause issues with the network manager/wpa authentication so it can be fixed.  I will post updates here as I find out more.

---

### Post by kntbrat on 2009-06-09
Hello, let me say quick that I am a newbie... like REALLY NEWBIE.  I know nothing about what I'm doing here but I'm very much willing to learn.  I've been trying to follow the instructions here on getting my USB Adapter to work but I can't seem to get past the first instruction.  Here's what I get when I type in the second code

                                 [FONT=Courier 10 Pitch][SIZE=2]root@*******-laptop:~# wget [http://www.ralink.com.tw/data/driver/2008_0925_RT2870_Linux_STA-v1.4.0.0.tar.bz2](http://www.ralink.com.tw/data/driver/2008_0925_RT2870_Linux_STA-v1.4.0.0.tar.bz2) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]--2009-06-09 01:56:20--  [http://www.ralink.com.tw/data/driver/2008_0925_RT2870_Linux_STA-v1.4.0.0.tar.bz2](http://www.ralink.com.tw/data/driver/2008_0925_RT2870_Linux_STA-v1.4.0.0.tar.bz2) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]Resolving [www.ralink.com.tw]("http://www.ralink.com.tw")... 192.72.83.242 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]Connecting to [www.ralink.com.tw|192.72.83.242|:80]("http://www.ralink.com.tw%7C192.72.83.242%7C:80")... connected. [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]HTTP request sent, awaiting response... 404 Not Found [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]2009-06-09 01:56:21 ERROR 404: Not Found. [/SIZE][/FONT]
 
I've typed this in three times and have gotten the same message.  What am I doing wrong?

---

### Post by jimbob on 2009-06-09
I just tried the wget and got the same result.  Looks to me like they have removed that particular file from their server.  Perhaps you can get it from someone here on the forum.  Or else wait and try again tomorrow.

---

### Post by baw4h on 2009-06-09
[http://www.ralink.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2](http://www.ralink.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2)
It's underscore, not a dash, after Linux_STA

---

### Post by jtx0 on 2009-06-10
I've now installed all updates except the FireFox 3.0.10 ones (five of them) on 9.04 i386 and my wireless is working flawlessly. I have submitted a bug to launchpad.net #385750 [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/385750](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/385750).

---

### Post by moocow1452 on 2009-06-14
Re-editing. I've narrowed down the problem to step 6, where the errors start flowing in. 

```
root@anna-laptop:~/2008_0925_RT2870_Linux_STA_v1.4.0.0#  make && make install
make -C tools
make[1]: Entering directory `/root/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/root/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
/root/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.28-6-powerpc/build SUBDIRS=/root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-6-powerpc'
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/md5.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/mlme.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_wep.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/action.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data.o
/root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data.c: In function &#8216;RTMP_FillTxBlkInfo&#8217;:
/root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data.c:713: warning: label &#8216;FillTxBlkErr&#8217; defined but not used
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_tkip.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_sync.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/eeprom.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_info.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_wpa.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/dfs.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/spectrum.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/assoc.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/aironet.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/auth.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sanity.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/rtmp_data.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/connect.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/wpa.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_linux.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/ba_action.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/2870_main_dev.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/2870_rtmp_init.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtusb_io.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtusb_bulk.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtusb_data.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data_2870.o
  LD [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/rt2870sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: Found 1 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/rt2870sta.mod.o
  LD [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/rt2870sta.ko
ld: arch/powerpc/lib/crtsavres.o: No such file: No such file or directory
make[2]: *** [/root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/rt2870sta.ko] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-6-powerpc'
make: *** [LINUX] Error 2

``` 

Anything?

---

### Post by radixor on 2009-06-15
Confirmation that the ra3070sta drivers are the ones that support the LinkSys WUSGB54GC v3. The installation is a bit different than the original instructions.

Fewer things that are better:
 -- Overall stronger signal
 -- The light actually lights up on the usb stick
 -- 1mpbs increase with default settings 


Some things i've noticed though, is that I've placed my laptop (running Windows Vista Home with wireless) next to my desktop (running 9.04 ubuntu with WUSGB54GC v3.0) and I ran beta.speedtest.net for both, it seems that the laptop was getting an average of 9Mbps while my desktop was getting 1.67Mpbs. 

I think there are still some minor tweaks that need to take place...

[update]
After some various tests, it looks much more stable, I'm getting roughly 5-6Mbps instead of the 0.6Mpbs I was getting with the 1.4.4.0 drivers.

---

### Post by radixor on 2009-06-15
> **moocow1452 said:**
> Re-editing. I've narrowed down the problem to step 6, where the errors start flowing in. 

```
root@anna-laptop:~/2008_0925_RT2870_Linux_STA_v1.4.0.0#  make && make install
make -C tools
make[1]: Entering directory `/root/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/root/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
/root/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.28-6-powerpc/build SUBDIRS=/root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-6-powerpc'
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/md5.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/mlme.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_wep.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/action.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data.o
/root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data.c: In function &#8216;RTMP_FillTxBlkInfo&#8217;:
/root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data.c:713: warning: label &#8216;FillTxBlkErr&#8217; defined but not used
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_tkip.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_sync.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/eeprom.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_info.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_wpa.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/dfs.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/spectrum.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/assoc.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/aironet.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/auth.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sanity.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/rtmp_data.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/connect.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/wpa.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_linux.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/ba_action.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/2870_main_dev.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/2870_rtmp_init.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtusb_io.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtusb_bulk.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtusb_data.o
  CC [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data_2870.o
  LD [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/rt2870sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: Found 1 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/rt2870sta.mod.o
  LD [M]  /root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/rt2870sta.ko
ld: arch/powerpc/lib/crtsavres.o: No such file: No such file or directory
make[2]: *** [/root/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/rt2870sta.ko] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-6-powerpc'
make: *** [LINUX] Error 2

``` 

Anything?

Hmm...what distro are you running? ```
linux-headers-2.6.28-6-powerpc
``` make for a highly interesting kernel build..

Anyway, do this to see if this resolves your issue:
```

cd /lib/modules/`uname -r`/
time make arch/powerpc/lib/crtsavres.o

```

if that doesn't work do this
```

cd ~/2008_0925_RT2870_Linux_STA_v1.4.0.0/
time make arch/powerpc/lib/crtsavres.o

```

hth

---

### Post by radixor on 2009-06-15
> **jtx0 said:**
> I just did a clean install of Ubuntu 9.04 i386 32-bit on my machine to test.  Based on others' comments I didn't do any of the initial updates (105 of them).  I installed the 1.4.0 drivers based on the instructions in this thread and connected on WPA2 AES no problems through Network Manager.  Thanks for the good work by Radixor.  It would seem that one of those 105 updates impacts the WPA/WPA2 components of Network Manager and WPA Supplicant.  I'm not sure I will go through installing them one at a time to figure that out yet as I will probably celebrate a bit of WiFi connectivity for a while.

Glad you figured it out! Looks like the initial updates might've been the problem?

---

### Post by radixor on 2009-06-16
Wow, guys, I just went through my instructions, I made a huge huge huge huge mistake in my instructions. Which is why I bet most people were having trouble authenticating...

Step 5 read:

```
 perl -p -i.old -e 's/(HAS*WPA*SUPPLICANT*=)y/{$1}n/g' os/linux/config.mk
```

It should've read
```
 perl -p -i.old -e 's/(HAS*WPA*SUPPLICANT*=)n/{$1}y/g' os/linux/config.mk
```

This would've caused the problems with WPA supplicant and WPA/WPA2 connectivity. I sincerely apologize. I'm surprised no one caught this mistake!

The perl code reads:

"perl, please in place edit 'os/linux/config.mk' but back up the old file by copying it and adding a .old extension; find all lines that match HAS*WPA*SUPPLICANT*=n (matches HAS_WPA_SUPPLICANT and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT) and replace it with HAS*WPA*SUPPLICANT*=y (The {$1} will be interpolated to fit whatever perl matched)."

I updated the steps in my original post. If you were having trouble authenticating, please let me know and I'll do all I can to help you.

---

### Post by sandy8925 on 2009-06-18
Thanks for the instructions; you are a real savior! Tried it out with the 1.4.0.0 drivers but didn't work THen tried compiling rt2870 drivers but still didn't work. Now will try with rt3070 drivers.

 By the way can someone please confirm exactly which chipset it is ? I've been searching and one site says 2501 another says 2587 and yet another says 2870 and here finally 3070. Could someone please clear that up without any doubt ?

---

### Post by radixor on 2009-06-18
According to:
[https://fjallfoss.fcc.gov/oetcf/eas/reports/ViewExhibitReport.cfm?mode=Exhibits&RequestTimeout=500&calledFromFrame=N&application_id=327783&fcc_id=%27Q87-WUSB54GCV3%27](https://fjallfoss.fcc.gov/oetcf/eas/reports/ViewExhibitReport.cfm?mode=Exhibits&RequestTimeout=500&calledFromFrame=N&application_id=327783&fcc_id=%27Q87-WUSB54GCV3%27)

The FCC says the chip is RT2070L, which is supported by the RT2070/RT3070 chip family.

RALINK did a terrible job supporting this dongle, as evidenced by this post:

[http://lists.rpmfusion.org/pipermail/rpmfusion-developers/2009-January/003498.html](http://lists.rpmfusion.org/pipermail/rpmfusion-developers/2009-January/003498.html)

Some reports from [http://rt2x00.serialmonkey.com:](http://rt2x00.serialmonkey.com:)

[http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=5245](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=5245)

Quote:
> I ripped open the dongle and the chip is a RT2070L.

Another interesting thread:

[http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=5136&hilit=RT2070](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=5136&hilit=RT2070)

All proof and evidence points that this is supported by the RT3070 driver.

---

### Post by jimbob on 2009-06-18
> ralink did a terrible job supporting this dongle, as evidenced by this post:

+1

---

### Post by sandy8925 on 2009-06-19
Ok thanks a lot. So will the rt3070 drivers work with it then ?

---

### Post by radixor on 2009-06-19
If you follow the steps I show you above, the driver should work fine. I had better luck, however, with the rt2870sta.dat that came from the rt2870 drivers instead of the rt3070 drivers

---

### Post by sandy8925 on 2009-06-19
I tried installing using the drivers you mentioned in the first post (1.4.0.0 i think). It didn't work. I executed   modinfo rt2870sta   and there were a bunch of stuff with the Id's listed ( the device id's and manufacturer id's ). My device has the id 1737:0077 and it wasn't listed there.

---

### Post by radixor on 2009-06-19
Please post your modinfo, I'll see what I can find out. 

Type in ```
modinfo ra2870sta
``` and post it here

You most likely didn't execute the cp command I had in step 7 or so.

---

### Post by AkaChan83 on 2009-06-20
So I've tried this whole process twice.  Both times everything went smoothly with zero errors but I'm still not finding any wireless networks.

Things I've done:

-Result of iwlist ra0 scan (I'm typing all of my results on my other laptop since I can't connect to the internet on my desktop:) ) :  
  ra0 Interface doesn't support scanning

-Changed "managed=false" to "managed=true" in nm-system-settings

-Result from lshw -class network:
  Too much to type :) But it only returns info for the ethernet card I have, nothing about any USB adapter...

Thoughts?

---

### Post by radixor on 2009-06-20
I need to see a few results before I can make any suggestions:

Try typing ```
lsmod
```

```
modinfo rt2870sta
```

```
/bin/ls -ltr /etc/Wireless/*
```

---

### Post by AkaChan83 on 2009-06-20
What are you looking for from lsmod? I have to type everything in by hand and there's a ton of things that come up..


modinfo rt2870sta returns the following:
filename:  /lib/modules/2.6.18-11-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:  1.4.0.0
license: GPL
description: rt2870 Wireless Lan Linux Driver
srcversion: 10297FA6A454E3CE8D2FAFC
then a bunch of alias:  

/bin/ls -ltr /etc/Wireless/*  returns:
-rw-r-r--r-- 1 root root 748 2009-06-20 09:55 RT2870STA.dat


Thanks bunches :-D

---

### Post by radixor on 2009-06-20
> **AkaChan83 said:**
> What are you looking for from lsmod? I have to type everything in by hand and there's a ton of things that come up..


modinfo rt2870sta returns the following:
filename:  /lib/modules/2.6.18-11-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:  1.4.0.0
license: GPL
description: rt2870 Wireless Lan Linux Driver
srcversion: 10297FA6A454E3CE8D2FAFC
then a bunch of alias:  

/bin/ls -ltr /etc/Wireless/*  returns:
-rw-r-r--r-- 1 root root 748 2009-06-20 09:55 RT2870STA.dat


Thanks bunches :-D

You did not type this command in (step #7) in my original instructions:


[FONT="Courier New"] cp -p /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2870sta.ko /lib/modules/`uname -r`/updates/[/FONT]

What this command does is it copies the [FONT="Courier New"]rt2870sta.ko[/FONT] that you built (by executing the ```
make
``` command) and places it in your [FONT="Courier New"]/lib/modules/`uname -r`/updates [/FONT]folder.

After you are sure you copied the  [FONT="Courier New"]rt2870sta.ko[/FONT] to the right folder, you need to execute this command:
```
depmod -a
```


This is what is needed! Right now, you're loading the pre-built linux drivers that come with Ubuntu, which is why you are unable to see the wireless networks.

---

### Post by AkaChan83 on 2009-06-20
Ugh, ok I didn't do step #5 on this install (did a clean install of jaunty and tried it again).  I went back and did it but the adapter still isn't working...

I'm getting the same output for the commands I ran last time :(

---

### Post by radixor on 2009-06-20
Did you reboot? You need to reboot once you do ```
depmod -a
```

Please do a:

```
/bin/ls -ltr /lib/modules/`uname -r`/updates/
```

And paste me the output.

Thanks!

---

### Post by AkaChan83 on 2009-06-20
/bin/ls -ltr/lib/modules/'uname -r'/updates outputs: 
--rw-r--r-- 1 root root 611918 2009-06-20 09:53 /lib/modules/2.6.28-11-generic/updates

---

### Post by radixor on 2009-06-20
> **AkaChan83 said:**
> /bin/ls -ltr/lib/modules/'uname -r'/updates outputs: 
--rw-r--r-- 1 root root 611918 2009-06-20 09:53 /lib/modules/2.6.28-11-generic/updates

Ah! I see the problem, the updates folder isn't created, so what ended up happening is that the file was copied as updates.

What you need to do is this:

```

cd /lib/modules/`uname -r`/
sudo mv updates rt2870sta.ko
sudo mkdir updates
sudo mv rt2870sta.ko updates/

```

After you do this, run
```

depmod -a

```

After that, please post the output of:
```

ls -ltr updates/

```
Thanks!!

---

### Post by AkaChan83 on 2009-06-20
okie dokie...output of ls -ltr updates:
-rw-r--r-- 1 root root 611918 2009-06-20 09:53 rt2870sta.ko

---

### Post by radixor on 2009-06-20
> **AkaChan83 said:**
> okie dokie...output of ls -ltr updates:
-rw-r--r-- 1 root root 611918 2009-06-20 09:53 rt2870sta.ko

Fantastic. Reboot now and you should be able to see your wireless networks in NetworkManager.

---

### Post by AkaChan83 on 2009-06-20
OMG!!! radixor, will you marry me??!!! i'm up and running!!!

Thank you soooooooo much!!!

---

### Post by radixor on 2009-06-20
> **AkaChan83 said:**
> OMG!!! radixor, will you marry me??!!! i'm up and running!!!

Thank you soooooooo much!!!

Congratulations ;) Enjoy!

---

### Post by jimbob on 2009-06-22
Radixor, you are a genius!! 

  I finally got around to trying to get my rt3070 chip to work with WPA2 encryption and by following your procedure to the letter by golly, IT WORKED!

Thanks so much.  The only problem I had was with the perl command.  It did not change the config.mk file at all - even the second time I ran it, so I resorted to vi.  I am not familiar with perl at all but it appears to be much like a sed command to replace the 'n' with a 'y' in two places.  I used copy and paste so I don't think it was my typing.  Doesn't bother me enough to learn perl though.

---

### Post by sandy8925 on 2009-06-24
Here's the modinfo output.I know I'm very late in replying.

filename:       /lib/modules/2.6.28-13-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        1.4.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     10297FA6A454E3CE8D2FAFC
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.28-13-generic SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)

---

### Post by jjmcc1 on 2009-06-24
I followed the procedure (I think/hope) and I am still having some problems.  I can see the wireless networks from network manager, but I can not seem to get access.  It keeps trying to connect but without success.

Here are some of the outputs that radixor asked of others suffering problems.

Any help or insight is greatly appreciated.


lsmod

```
Module                  Size  Used by
isofs                  43688  1 
udf                    92584  0 
crc_itu_t              10496  1 udf
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
vboxnetflt            110316  0 
vboxdrv              1704748  1 vboxnetflt
input_polldev          12688  0 
video                  29204  0 
output                 11648  1 video
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557492  3 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78792  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_nforce2            16136  0 
nvidia               8123768  36 
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
k8temp                 13440  0 
rt2870sta             556648  0 
psmouse                64028  0 
serio_raw              14468  0 
pcspkr                 11136  0 
usb_storage           115392  0 
forcedeth              68368  0 
ohci1394               42036  0 
ieee1394              108288  1 ohci1394
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
compcache              13808  1 
lzo_decompress         11264  1 compcache
lzo_compress           11264  1 compcache
tlsf                   15392  1 compcache

```modinfo rt2870sta```
filename:       /lib/modules/2.6.28-13-generic/updates/rt2870sta.ko
version:        1.4.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     E00168480A46C5501E5B1FD
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.28-13-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)

```/bin/ls -ltr /etc/Wireless/*```
-rw-r--r-- 1 root root 746 2009-06-24 13:47 RT2870STA.dat~
-rw-r--r-- 1 root root 746 2009-06-24 14:42 RT2870STA.dat


```

---

### Post by jimbob on 2009-06-24
sandy8925:  Your modinfo does not show the 1737:0077 that is provided in the substitute rt2870.h module (unless I missed it).

When your module is plugged in and you do an lsusb does it show this line: 
Bus 001 Device 002: ID 1737:0077 Linksys

Just a thought.

---

### Post by sandy8925 on 2009-06-25
Yeah it does. Also in the driver cd there is an inf file named rt2870.inf

I'm guessing the chip is a 2870 and not 3070.

---

### Post by wizme on 2009-06-27
Hi,

is there any way i can contact you, [radixor]("http://www.uluga.ubuntuforums.org/member.php?u=388185")? like msn or something

---

### Post by sandy8925 on 2009-06-28
HEy radixor could you please tell me exactly what step 5 does ? I think it's not getting done so I'll have to check and do the changes manually if needed. Also should I replace the header file if I use the newer drivers (Such as 2.1.1.0) too ?

One last question: my SSID is actually two words so should I put quotes around them in the .dat file ?

---

### Post by sandy8925 on 2009-06-28
Hey I just discovered that there's this WebUI file underneath the 2.1.2.0 drivers for the rt2870 . I downloaded it and it contains the driver files as well and an install script I think. Has anyone checked that out ?

---

### Post by hoodies on 2009-07-03
can some one please please please help me figure this out im so new to this its not even funny. i know it can be done just cant figure it out. i dont even know how to compile from source yet. i have ubuntu 9.04 jantuy with no up dates cause i cant connect to the INTERNET and my router is up stairs shareing its signal with all my windows computers just fine.  my linux feels left out. step by step would be nice  like really step by step i need  need need this to work!

---

### Post by radixor on 2009-07-03
> **sandy8925 said:**
> Yeah it does. Also in the driver cd there is an inf file named rt2870.inf

I'm guessing the chip is a 2870 and not 3070.

Hi Sandy,
Your modinfo, as Jimbob has told you, does not show the v1737p0077. This means that you *did not* replace the attached header file found in my original post. The reason that this header file is important is that it allows the driver to recognize your usb "v1737p0077" dongle.

Please ensure that this header file replaces the original one as in my original post. Re-make, re-install, and reboot. 

If you installed it correct, when you do
```
modinfo rt2870sta | grep v1737p0077
``` you should see ONE ENTRY.

If you're still having issues, re-post the various 
```
modinfo rt2870sta
```
```
lsusb 
```


Your second comment:
> **sandy8925 said:**
> 
HEy radixor could you please tell me exactly what step 5 does ? I think it's not getting done so I'll have to check and do the changes manually if needed. Also should I replace the header file if I use the newer drivers (Such as 2.1.1.0) too ?

One last question: my SSID is actually two words so should I put quotes around them in the .dat file ?


The new 2.1.1.0 drivers will not work for you, only the rt3070sta, but I will write another writeup for that when I get a chance. Step 5 does an in-place edit to replace the USE_WPA_SUPPLICANT=n with a USE_WPA_SUPPLICANT=yes in [FONT="Courier New"]os/linux/config.mk[/FONT] 

Thanks!
Radixor

---

### Post by radixor on 2009-07-03
> **jjmcc1 said:**
> I followed the procedure (I think/hope) and I am still having some problems.  I can see the wireless networks from network manager, but I can not seem to get access.  It keeps trying to connect but without success.

Here are some of the outputs that radixor asked of others suffering problems.

Any help or insight is greatly appreciated.


lsmod

```
Module                  Size  Used by
isofs                  43688  1 
udf                    92584  0 
crc_itu_t              10496  1 udf
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
vboxnetflt            110316  0 
vboxdrv              1704748  1 vboxnetflt
input_polldev          12688  0 
video                  29204  0 
output                 11648  1 video
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557492  3 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78792  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_nforce2            16136  0 
nvidia               8123768  36 
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
k8temp                 13440  0 
rt2870sta             556648  0 
psmouse                64028  0 
serio_raw              14468  0 
pcspkr                 11136  0 
usb_storage           115392  0 
forcedeth              68368  0 
ohci1394               42036  0 
ieee1394              108288  1 ohci1394
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
compcache              13808  1 
lzo_decompress         11264  1 compcache
lzo_compress           11264  1 compcache
tlsf                   15392  1 compcache

```modinfo rt2870sta```
filename:       /lib/modules/2.6.28-13-generic/updates/rt2870sta.ko
version:        1.4.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     E00168480A46C5501E5B1FD
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.28-13-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)

```/bin/ls -ltr /etc/Wireless/*```
-rw-r--r-- 1 root root 746 2009-06-24 13:47 RT2870STA.dat~
-rw-r--r-- 1 root root 746 2009-06-24 14:42 RT2870STA.dat


```

I'm guessing you did follow the procedure, but I want to know, can you do a
```
lsusb
```
```
iwconfig
```
```
ifconfig
```
 and post the following output here?

The reason I'm suspicious is that your drivers look fine for a v1737p0077, but that means when the dongle is inserted into the usb port, the 
```
rt2870sta             556648  0 
``` should have a 1 at the end; the one signifies that the driver is being used

I am suspecting something else..since you're seeing wireless networks.

Thanks,
Radixor

---

### Post by radixor on 2009-07-03
> **hoodies said:**
> can some one please please please help me figure this out im so new to this its not even funny. i know it can be done just cant figure it out. i dont even know how to compile from source yet. i have ubuntu 9.04 jantuy with no up dates cause i cant connect to the INTERNET and my router is up stairs shareing its signal with all my windows computers just fine.  my linux feels left out. step by step would be nice  like really step by step i need  need need this to work!

You should follow the steps posted here
[http://ubuntuforums.org/showthread.php?t=1155941](http://ubuntuforums.org/showthread.php?t=1155941)

If you get any errors, post those errors as well.
Thanks.

---

### Post by Animejeroe on 2009-07-06
Hey guys - 1st off - Radixor - you are incredible. It takes something special to provide the thorough support you provide through this forum. Major KUDOS to you.

With that being said... 

I followed your steps to completion. I am able to see all kinds of networks, but cannot connect to mine. I only have MAC filtering. To confirm, I even turned that off. Still, only can connect hardwired. I _see_ the networks, but cannot get into it.
I saw that some had that same issue - but found nothing about closure. Oddly enough, I followed the networking troubleshooting steps with the up/down steps, and get the ability to ping a website, but no real use (no webpages would load). Can you please offer me a direction to go to get some resolution?
Problem is this - I am too stubborn to let this go. I can always run out and get a different adaptor, but thats the fun of Linux, right?

---

### Post by radixor on 2009-07-06
> **Animejeroe said:**
> Hey guys - 1st off - Radixor - you are incredible. It takes something special to provide the thorough support you provide through this forum. Major KUDOS to you.

With that being said... 

I followed your steps to completion. I am able to see all kinds of networks, but cannot connect to mine. I only have MAC filtering. To confirm, I even turned that off. Still, only can connect hardwired. I _see_ the networks, but cannot get into it.
I saw that some had that same issue - but found nothing about closure. Oddly enough, I followed the networking troubleshooting steps with the up/down steps, and get the ability to ping a website, but no real use (no webpages would load). Can you please offer me a direction to go to get some resolution?
Problem is this - I am too stubborn to let this go. I can always run out and get a different adaptor, but thats the fun of Linux, right?

Alright, so you do not have authentication enabled? Let's take it a step further, can you attempt to connect to a network and paste for me what your ```
dmesg
``` says while you connect. 

Please also paste for me what /var/log/syslog says while you connect? If you are unsure what to do, something like this would work
```
 tail -100 /var/log/syslog 
``` and paste me the output.

Please also do these and paste it here: 
```
sudo lshw -C network
```
```
lsusb
```
```
modinfo rt2870sta
```
```
lsmod | grep rt2870sta
```
Thanks very much,
Radixor 

P.S. Thanks for the kind words. Ubuntu and the FOSS movement thrives on community help, without this, we would be no better than Microsoft.

P.P.S. - I no longer use NetworkManager, I find that Wicd is a better wireless manager. Something to keep in mind is
```
sudo apt-get install wicd
``` and reboot.

---

### Post by jjmcc1 on 2009-07-06
Radixor, here is the output  you requested.  Let me reiterate what others have already said... you are awesome!

lsusb
```
Bus 001 Device 004: ID 1737:0077 Linksys 
Bus 001 Device 003: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-44 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:24:8c:21:9e:25  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:254 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ra0       Link encap:Ethernet  HWaddr 00:23:69:72:0b:fc  
          inet6 addr: fe80::223:69ff:fe72:bfc/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1592 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1010 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:417814 (417.8 KB)  TX bytes:73556 (73.5 KB)

```

---

### Post by Animejeroe on 2009-07-06
> Alright, so you do not have authentication enabled? Let's take it a step further, can you attempt to connect to a network and paste for me what your ```
dmesg
``` says while you connect. 


Okay - here is your data :

...REVISION...

I decided to follow your advice AFTER getting all the data - and posting it. I removed it, since I fixed it with your extended advice. I installed WICD. It seemed to remove my driver info, so I had to redo the steps on page 1, but after completion - BING!! - online wirelessly. 

THANK YOU RADIXOR! I agree that teamwork makes Linux what it is. That and determination. *grin*

THANK YOU AGAIN!
AJ

---

### Post by JordanL on 2009-07-11
Hey all. Just wanna thank radixor and jimbob, without you guys I would have never made this work. However to help out all of you I'm gonna place my instructions here that worked first shot with the Linksys WUSB54gc v3 dongle. Hopefully this clears up some things for people, it took me allot of jumping around between posts to get it all worked out. Props goes to radixor and jimbob for this, I'm just consolidating it here.

**Step 1**
Check which chipset it is:
```
lsusb
```
For me it returned
```
Bus 001 Device 002: ID 1737:0077 Linksys
```
the 1737:0077 is the important piece there if you plan to follow my steps.

**Step 2**
```
sudo -i
```

**Step 3**
```
wget http://www.ralinktech.com.tw/data/drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2
```
We are using the 2.1.1.0 driver for rt3070, works perfectly for me

**Step 4**
```
tar xjf 2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2
```
```
cd 2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2
```
**Step 5**
This is where you want to implement some of jimbobs suggestions from [http://ubuntuforums.org/showpost.php?p=7295449&postcount=25](http://ubuntuforums.org/showpost.php?p=7295449&postcount=25) this post.
```
gedit os/linux/usb_main_dev.c
```
in there add this line (with the rest of the similar ones)
```
{USB_DEVICE(0x1737,0x0077)} /* Linksys WUSB54GC */
```
and then
```
gedit os/linux/config.mk
```
change all the stuff to do with WPA_SUPPLICANT to y (I also changed HAS_AUTO_CH_SELECT to y as well, not sure if it made any significant difference)
then:
```
gedit /etc/modules
``` (it may be called modules.conf but mine didn't have an extension) and add this line
```
alias ra0 rt3070sta
```
[B]Step 6[B]
in the file i downloaded from ralink the .dat file was called RT2870sta.dat not RT3070 as jimbob points out but all the same do this:
```
gedit RT2870.dat
``` 
if your using wpa2/wpa set AUTHMODE:WPA2 EncrypType:TKIP and fill in your paskey and SSID.

**Step 7**
```
make && make install
```

**Step 8**
make sure lib/modules/'uname -r'/updates folder exists or you will get a 'updates is a folder' error
(note the change to rt3070sta instead of 2870 like radixor's original post)
```
cp -p /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt3070sta.ko /lib/modules/`uname -r`/updates/
```

**Step 9**
```
depmod -a
```

**Step 10**
as jimbob points out you need to move the rt2870sta.dat file to the right folder. Either use cp, or be lazy and sudo nautilus so you can root move around stuff with a gui 
```
cp -f /etc/Wireless/RT3070STA/RT2780STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
```

**Step 11**
```
echo "ifconfig ra0 inet up" >> /etc/init.d/rc.local
```

**Step 12**
Reboot.

**Step 13**
for network manager go
```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```
set managed=false to true
```
sudo killall nm-system-settings
```

These are the exact steps I did on a fresh install of 9.04 64bit. I now have 100% signal strength, fast connection to wpa2 encrypted apple airport extreme, speed of 65Mb/s connection (according to connection manager) and im downloading files at 300kbps on dsl. ANND the green light works :) Hope this helps! Thanks again goes to radixor and jimbob!!

---

### Post by JordanL on 2009-07-11
As I soon found out, upgrading your kernel headers will break this. I think this is mainly because the updates folder doesn't exist in the new kernel folder (step 8 ) regardless get back into the install folder and go make uninstall... then make && make install and pretty much adjust step 8  for new kernel path and the rest should already be configured from before. Worked fine for me. If I find time I might write a bash script to automate this all.

---

### Post by ducksun43 on 2009-07-11
[http://sunoano.name/ws/public_xhtml/ggm.html#wifi_and_debian](http://sunoano.name/ws/public_xhtml/ggm.html#wifi_and_debian) this one helped me a lot with setting up wifi. Imho it also answeres the problems here.

---

### Post by scarfays on 2009-07-12
hello  
 I buy a USB stick ZIONCOM WL0162 with RT3070L chipset and RT3070 drivers  
 I test the drivers to install Ralink 2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2

```
 wget http://www.ralinktech.com.tw/data/drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2   
```
```
 tar xjf 2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2  
```
```
 cd 2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2  
```
```
 gedit os / linux / config.mk  
```
 I change in Config.mk by = n = y 
 ```
 # ifdef WPA_SUPPLICANT_SUPPORT 
 # Support wpa_supplicant 
 HAS_WPA_SUPPLICANT = y 
 # endif / / WPA_SUPPLICANT_SUPPORT / / 

 # ifdef NATIVE_WPA_SUPPLICANT_SUPPORT 
 # Support Native WpaSupplicant for Network Maganga 
 HAS_NATIVE_WPA_SUPPLICANT_SUPPORT = y 
 # endif / / NATIVE_WPA_SUPPLICANT_SUPPORT / / 
```
```
  gedit / etc / modules 
```
[LEFT]I add in modules: 
 "Alias ra0 rt3070sta" 
 Close and save 
 after I install and compile[/LEFT]

```
 sudo make & & sudo make install  
```
after I go to the folder: 
  etc/wireless/RT3070sta/RT2870sta.dat 
 here it is necessary to change the file RT3070STA by RT2870STA 
 I use sudo nautilus to change
```
 etc/Wireless/RT2870STA/RT2870STA.dat  
```
after I finished with:
```
  [LEFT]sudo modprobe RT3070STA[/LEFT]  
```
```
  [LEFT]sudo ifconfig ra0 up[/LEFT]  
```
[LEFT]especially for me I use Aircrack-ng and airodump-ng and 
 but arrive in airodump-ng it just scans the channel 11, not the other channel 
 you had can be a solution to my problem? 
 I must know I am not using network-manager 
 I just want it to work on airodump-ng and aircrack-ng 
 I really need help 
 sorry for my English, which is not good 
 Please help me thank you[/LEFT]

---

### Post by sandy8925 on 2009-07-12
YES!!!!! finally got it working ! thank you so much !

(fireworks in the sky accompanied by beautiful music in the background)

---

### Post by scarfays on 2009-07-14
hello 
I really need help this time 
I have it install the RT3070 drivers but there is always the drivers install RT2870 
impossible to install! 
how can I do? 
how to clear the RT2870 drivers for the RT3070 finally put in place?

---

### Post by Epson_Stylus on 2009-07-17
Ubuntu 9.04 Jaunty  64 bit

I had the issue with the version 3 device and consequently returned it after I couldn't sift through the guide process (I'm a noob  =P)

Incidentally, if anyone is looking for a way to get non version 3 WUSB54GC devices, try some non computer stores.  I got mine in the computer section at Target.  It was, seeing as how they do not stock up to date parts, version 1.3 with the rt73usb chipset.  It worked right out of the box without even needing the CD.

In short, check general stores since they rarely keep stock and it seems like a popular model.  

_**Also, to those seeking non v3 devices, I found that the USB card pictured on the  version 1.3 box is White for version and black on the version 3.**_

---

### Post by jimbob on 2009-07-18
I wonder if there will come a day that the v3 version driver for the rt3070 chip will be included as part of the Ubuntu distribution.

  Sure would be nice but I guess that's the "fun" of Linux, right?

---

### Post by DaGodFuddah on 2009-07-18
I got the wireless adapter to recognize wireless access points (I know because Ubuntu tells me that it has detected the presence of access points, including my router) but unfortunately though, when I try to connect to my router at home (which also displays that it has a strong signal) ubuntu just "attempts" to connect, and keeps showing me a dialog box telling me to enter the password to the router. All it does basically is that it tries to connect, but never gives me any internet connection.

Anyways, I'm using Ubuntu 9.04, my wireless adapter is a Linksys Compact Wireless-G USB Adapter (Model No. WUSB54GC Ver. 3), and my router is a 2Wire router (given to me for free by telus), and the connection is via WEP and not WPA (I know because that's how I connect on windows), and I'm 100% sure the password I'm entering is correct.

The thing is though, I skipped step 9 of the tutorial. Does that have anything to do with it?

---

### Post by hipogrito on 2009-07-23
Hello,

First, thanks a lot for the instructions.

I have a similar problem as few others... my Ubuntu sees all the networks now but when it tries to connect to mine it tries and tries and tries but never connect... I tried with WEP, WPA and even with Nothing, but it just cannot get thru...

I have a Linksys router and a brand new Linksys antenna... 

At least this is a progress to my previous state, where I was trying to use the build in wireless antenna of my laptop, Atheros drivers, and I could not even see the wireless networks.

So, I guess that I am missing something... maybe basic...?

All the steps were executed without problems... the channel is properly set... everything seems fine.... but it isn't...


Any hint? My wife is freaking out with a 10 meter cable through the house :-D


Thanks!!!!!!!!!!!!

Kind regards,
Fran

---

### Post by hipogrito on 2009-07-26
Hi,

Here you have some details of my configuration... any idea is welcomed... I have tried everything and It seems I cannot connect.

Ubuntu 9.04
Wireless:WUSB54GC v. 3

I'll try to be short...

I can see the networks around me:

```

sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:18:01:F8:9B:B1
                    ESSID:"HE4N4"
                    Mode:Managed
                    Channel:1
                    Quality:5/100  Signal level:-88 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
          Cell 02 - Address: 00:1A:70:D5:24:D0
                    ESSID:"EUF"
                    Mode:Managed
                    Channel:6
                    Quality:100/100  Signal level:-48 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:18:01:F9:17:DE
                    ESSID:"XVVO4"
                    Mode:Managed
                    Channel:11
                    Quality:15/100  Signal level:-84 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s

pan0      Interface doesn't support scanning.


```

EUF is mine.


When I try to connect I get this:


```

sudo wpa_supplicant -Dwext -ira0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'ra0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=3):
     45 55 46                                          EUF             
scan_ssid=0 (0x0)
proto: 0x2
key_mgmt: 0x2
auth_alg: 0x1
pairwise: 0x18
group: 0x18
PSK (ASCII passphrase) - hexdump_ascii(len=8): [REMOVED]

PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='EUF'
Initializing interface (2) 'ra0'
Interface ra0 set UP - waiting a second for the driver to complete initialization
SIOCGIWRANGE: WE(compiled)=22 WE(source)=14 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:23:69:e0:2d:41
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
Using existing control interface directory.
Added interface ra0
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds

```

So, it does not connect.


My configuration file is:

```

ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
	ssid="EUF"
	scan_ssid=0
	proto=WPA2
	key_mgmt=WPA-PSK
	auth_alg=OPEN
	pairwise=CCMP TKIP
	group=CCMP TKIP
	psk=9e59d...
}

```


Check that the driver is there...

```

lsmod|grep 'rt2870sta'
rt2870sta             502868  1 

```


If I have a 0 after the 502868 I can turn it on with:

```

sudo ifconfig ra0 up

```



I followed all the instructions of this post and several other posts... no luck yet but if I see the networks It must be close.... :D

Thank you very much!!

Kind regards,
Hipo

---

### Post by picochu on 2009-07-28
Hi guys, 
I had managed to get my EnGenius EUB-9703 running. I got it cheap at Carrefour for less than 20 SGD. It is using RT3070 and I got it running with WPA2 with iwpriv, I couldn't get it to work with WPA Supplicant. 

The commands are actually very simple:

ifconfig ra0 up
iwpriv  ra0 set NetworkType=Infra
iwpriv  ra0 set AuthMode=WPA2PSK
iwpriv  ra0 set EncrypType=TKIP
iwpriv  ra0 set SSID="your ssid"
iwpriv  ra0 set WPAPSK="your passphrase."
iwpriv  ra0 set SSID="your ssid"
dhclient ra0

---

### Post by hipogrito on 2009-08-01
Hello,

Finally I killed my Ubuntu and reinstall it from scratch... a couple of years of incremental updates leave your machine with a good amount of crap...

and.... I can CONNECT!!!!!!!!!!!!!!!!!!!! :D

Thank you very much for the help!

My next step is figuring out why every 2 minutes it prompts for the WPA password... I just have to click Ok, but it is pretty annoying.

Regards,
Hipo

---

### Post by jimbob on 2009-08-01
If you are using Network Manager you can try this to stop it from asking for a password continually:

Right click on nm-applet -> "Edit connection"
Go to the "Wireless" tab
Click on the wireless hotspot you want to automatically connect to
Click the "Edit" button
At the bottom of the window, you should see a tick box which says "Available to all users".
Tick it and click Apply!

---

### Post by hipogrito on 2009-08-01
Hi,

> **jimbob said:**
> If you are using Network Manager you can try this to stop it from asking for a password continually:

Right click on nm-applet -> "Edit connection"
Go to the "Wireless" tab
Click on the wireless hotspot you want to automatically connect to
Click the "Edit" button
At the bottom of the window, you should see a tick box which says "Available to all users".
Tick it and click Apply!

Thanks!

Regards,
hipo

---

### Post by Beyond014 on 2009-08-09
Thank for every one here, I finally got wireless network to work.
However, the connection information shows that the speed is 54Mb/s.
Is it too slow? How could I fix this?

I actually followed all the steps on page 1 and did some Wpa_supplicant tutorial.

---

### Post by jimbob on 2009-08-09
I think that's as good as 802.11g gets unless you have 802.11n equipment.

---

### Post by skdevnath on 2009-08-24
It worked for me... great tutorial. It is  complete too unless you do some mistake. I did 2 mistakes and I end up spending 4 hr due to that. I am listing them, just to make sure others don't do that.

1). I went ahead with ralink's lastes driver(2009), since I already downloaded on my machine as part of some other thread. I need to search USB devices data structure and add my USB device number. Even after that I can just see green light, but **iwlist **didn't return any network. 
2). Somehow the perl code provided in the tutorial didn't change the option to allow wpa_supplicant to control the card. So even though I was able to scan neighbor by networks and also I was able to connect using **iwpriv, iwconfig***, *I was still not able to use wpa_supplicant to connect.
:guitar::popcorn:

---

### Post by shad0w221 on 2009-08-25
hi, this is my first time using linux and i wanted to use my linksys WUSB54GC. i never dealt with linux or done any tinkering with any type of terminal in windows or mac, i got stuck on step 4 of the tutorial. do i replace that [FONT=Courier New]include/rt2870.h[/FONT] with rt2870.h? where do i find that? where is the "attached [FONT=Courier New]rt2870.h.tar.gz[/FONT]"?

also, in step 7, the 'uname -r', is that a placeholder for a name of a specific file? or is that what its actually supposed to be?

these are just a few questions i have now, hopefully i can get this usb adapter to work, it seems to be working based on responses from everyone on this thread, ill probably be coming back here, im a noob =p

---

### Post by grayhatter on 2009-09-03
The attached file is at the bottom of Post #2, it looks like you must be logged in to download....


I'm having problems getting the module to have the update required for the Linksys WUSB54gc.

Not sure where to go from here, any tips or hints welcome.

root@desktop-lnx:/home/user/wlan# modinfo rt2870sta | grep 1737
root@desktop-lnx:/home/user/wlan#

root@desktop-lnx:/home/janderson/wlan# cd /etc/Wireless
root@desktop-lnx:/etc/Wireless# ls
RT2870STA  RT2879STA

root@desktop-lnx:/etc/Wireless# lsmod | grep rt2870sta
rt2870sta             506324  0 

root@desktop-lnx:/etc/Wireless# ifconfig ra0 up
ra0: ERROR while getting interface flags: No such device

    
root@desktop-lnx:/etc/Wireless# cat /home/user/wlan/include/rt2870.h | grep Linksys
	{USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */		\
root@desktop-lnx:/etc/Wireless#

---

### Post by rkrawec on 2009-09-06
I know where i went wrong. In step seven, I created the 'uname -r' and updates directories. When I run the cp... script, I get the following error:
 
cp: cannot stat '/lib/modules/uname -r/kernal/drivers/net/wireless/rt2870sta.ko' : No such file or directory
 
This make sense in that I know there are no kernal/drivers/net/wireless directories. Did something go wrong when I ran the perl script? 
 
Any suggestions.
 
Ron
 
....
 
DUH!
 
Okay, do I substitute the output of uname -r as the directory between Modules and Kernal?   (At least I know uname -r is a command and condition). 
 
Ron

---

### Post by anant29 on 2009-09-12
Hello Radixor,

i just bought my wifi USB. WUSB54GV V3.
i was following the steps in the original post and i am stuck on step#5.

this is the output:
root@Tablet:/root/2008_0925_RT2870_Linux_STA_v1.4.0.0/include# perl -p -i.old -e 's/(HAS*WPA*SUPPLICANT*=)n/{$1}y/g' os/linux/config.mk
Can't open os/linux/config.mk: No such file or directory.

 i did a full update before i started with the steps. Is there something else that I have to do before I begin?

please advice.
thanks

---

### Post by anant29 on 2009-09-12
> **anant29 said:**
> Hello Radixor,

i just bought my wifi USB. WUSB54GV V3.
i was following the steps in the original post and i am stuck on step#5.

this is the output:
root@Tablet:/root/2008_0925_RT2870_Linux_STA_v1.4.0.0/include# perl -p -i.old -e 's/(HAS*WPA*SUPPLICANT*=)n/{$1}y/g' os/linux/config.mk
Can't open os/linux/config.mk: No such file or directory.

 i did a full update before i started with the steps. Is there something else that I have to do before I begin?

please advice.
thanks


this is resolved!! :D sorry.. my bad! :|

---

### Post by Sophism on 2009-09-12
I just picked up this USB card as well. The issue I am running into is I am unable to download any of the drivers linked in this thread from ralink.

Does anyone have the package that they can post in this thread?

---

### Post by anant29 on 2009-09-12
> **Sophism said:**
> I just picked up this USB card as well. The issue I am running into is I am unable to download any of the drivers linked in this thread from ralink.

Does anyone have the package that they can post in this thread?

[http://rapidshare.com/files/279284721/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.gz.html](http://rapidshare.com/files/279284721/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.gz.html)

thats the file.

---

### Post by mjkozak on 2009-09-20
Just wanted to say thanks, **radixor**!  Only hitch was having to vi a y in in place of the n because the perl didn't work. Thanks a million, man, great work!

---

### Post by crtaylor1970 on 2009-09-23
Hey all,
  I'm new at this and have come to a problem using my wusb54gc V.3 usb adapter with my pc using ubuntu 9.04. The report from lsusb:
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1737:0077 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00f9 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

The light on my adapter does not turn on and I've gone over the forums over and over again. Since this adapter did not plug and play it seems I may be having a driver problem. Only thing is that I cannot find anyplace to download a driver for this device at. (Keep getting 404 when I click on a link to download a driver for this device)
 
Network manager isn't showing anything up for wireless here at all and do not have wirless assistant as was shown in a tutorial. 

If you need any more info I can place it on here.
Thank you for any help with this.

---

### Post by Broolucks on 2009-09-23
> **anant29 said:**
> [http://rapidshare.com/files/279284721/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.gz.html](http://rapidshare.com/files/279284721/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.gz.html)

thats the file.

Unfortunately, the download link does not work anymore:

 "This file is neither allocated to a Premium Account, or a Collector's Account, and can therefore only be downloaded 10 times.
 

This limit is reached."


Could you/someone re-upload it somewhere? :(

---

### Post by nusntu on 2009-09-23
> **crtaylor1970 said:**
> Hey all,
I'm new at this and have come to a problem using my wusb54gc V.3 usb adapter with my pc using ubuntu 9.04. The report from lsusb:
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1737:0077 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00f9 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
The light on my adapter does not turn on and I've gone over the forums over and over again. Since this adapter did not plug and play it seems I may be having a driver problem. Only thing is that I cannot find anyplace to download a driver for this device at. (Keep getting 404 when I click on a link to download a driver for this device)
 
Network manager isn't showing anything up for wireless here at all and do not have wirless assistant as was shown in a tutorial. 
 
If you need any more info I can place it on here.
Thank you for any help with this.
 
I have the same problem. My card is never detected by the driver (ndiswrapper, rt73 or rt2870sta). Anyone can help to identify the problem?

---

### Post by Vincinzerei on 2009-09-27
Have the same problem.
Gone through the tutorial without problems
because not was able to get my hands on  1.4driver version i used v2.2.0.0
but found no wireless assistent or got any success getting wlan to run.
i like ubuntu but after using 12 hours with different "solutions" and still not working, i really get back to the point "coming back later when all works without have to be a linux crack"
The card is shown in the usb
ra0 scan get "ra0       Interface doesn't support scanning."
also the same problem with 
>>Using wpa_supplicant to connect!
Read this great tutorial/walk-through here: 
http://ubuntuforums.org/showthread.php?t=263136<<
no success but wpa supplicant is installed and configured like shown..

---

### Post by yobird42 on 2009-09-27
could someone re-up the rar please?

---

### Post by rorist on 2009-09-27
i have this device too, it is recognized in Karmic daily-build by the rt2x00 driver (rt2800usb) as interface wlan0, but link could not be established.

Maybe we should try the last version of rt2x00

---

### Post by kanibalv on 2009-09-27
I have a G60 laptop with atheros 5001, using kubuntu karmic, ath5k, but I can't see my wrt54g (ddwrt) router, my neighbor is on the list, it seem that could be a wpa_supplicant problem o WPA, but if I set my router to WEP, it not show eihther. No clue so far what's the problem, it's driving me crazy.:confused:

---

### Post by korkyboy on 2009-09-28
Hi there. I am having similar issues when trying to use this Wireless USB on ubuntu 9.04. I have (as far as I know) followed all steps shown by Radixor. 

lsusb:
us 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1737:0077 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 062a:0102 Creative Labs 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

iwlist ra0 scan

ra0        Interface doesn't support scanning.

ifconfig ra0 up
ra0: ERROR while getting interface flags: No such device
 
_lsmod_

infmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25360  0 
output                 11008  1 video
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         434100  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
joydev                 18496  0 
nvidia               7233756  36 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
pcspkr                 10496  0 
intel_agp              34108  0 
agpgart                42696  2 nvidia,intel_agp
usbhid                 42336  0 
ndiswrapper           193436  0 
floppy                 64324  0 
atl1                   40584  0 
mii                    13312  1 atl1
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

_modinfo:_
ilename:       /lib/modules/2.6.28-15-generic/updates/rt2870sta.ko
version:        2.2.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     FC3DC979BFDB82D40B53250
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.28-15-generic SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)

Any help, greatly appreciated!! This is driving me nuts!!!

---

### Post by Soulou on 2009-10-03
Hello,

I use karmic kernel (2.6.31-11-generic) and with it, i don't success to compile the driver :

```
make
make -C tools
make[1]: entrant dans le répertoire « /home/leo/Bureau/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools »
gcc -g bin2h.c -o bin2h
make[1]: quittant le répertoire « /home/leo/Bureau/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools »
/home/leo/Bureau/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/leo/Bureau/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/Makefile
make  -C  /lib/modules/2.6.31-11-generic/build SUBDIRS=/home/leo/Bureau/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.31-11-generic »
  CC [M]  /home/leo/Bureau/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.o
/home/leo/Bureau/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/leo/Bureau/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1510: error: ‘struct net_device’ has no member named ‘cred’
/home/leo/Bureau/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1510: error: ‘RTMP_OS_NETDEV_OP_HOOK’ has no member named ‘cred’
/home/leo/Bureau/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1511: error: ‘struct net_device’ has no member named ‘stop’
/home/leo/Bureau/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1512: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/leo/Bureau/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1513: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/leo/Bureau/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1519: error: ‘struct net_device’ has no member named ‘get_stats’
/home/leo/Bureau/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1553: error: ‘struct net_device’ has no member named ‘validate_addr’
make[2]: *** [/home/leo/Bureau/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.o] Erreur 1
make[1]: *** [_module_/home/leo/Bureau/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.31-11-generic »
make: *** [LINUX] Erreur 2

```

Has someone already do it ?

---

### Post by radixor on 2009-10-20
Original post has been updated to point to new link to download this file:
[SIZE="6"]**[COLOR="Red"][http://bit.ly/4pPyzx]("http://bit.ly/4pPyzx")[/COLOR]**[/SIZE]

HOWEVER, ralink has posted new link up on their website for [RT2870USB(RT2870/RT2770)]("http://bit.ly/1Ccl7c")

---

### Post by Kjeldgaard on 2009-10-21
Thank you very much!!!

My wifi usb dongle is now working!!! Now my problem is that when i add "alias ra0 rt2870sta" to etc/modules and "ifconcig ra0 inet up" to etc/init.d/rc.local then ubuntu "hangs" very long before getting to the login screen. So after a restart I have to run "modprobe rt2870sta" and then my wifi dongle works. How can I make it autostart whitout leaving ubuntu hanging.

---

### Post by bonhomme on 2009-10-24
Hi all,

I have this usb dongle working fine with jaunty, kernel  2.6.28-15-generic. However there was recently an update to 2.6.28-16-generic, which breaks it (since I have both kernels in my grub/menu.lst, I can boot the old one and it works, boot the new one, and it doesn't work, with no changes to anything in between).

When the updated kernel is booted, I get a set of diagnostics very similar to that posted by korkyboy previously:
[LIST]
[*]Linksys ID 1737:0077 shown by lsusb
[*]"ra0: ERROR while getting interface flags: No such device" returned by ifconfig ra0 inet up
[*] module not automatically loaded (doesn't appear in lsmod)
[*] if module manually loaded with modprobe, it's not used (Used by: 0 in lsmod); other commands return same errors
[*] lshw -C network does not list the wireless device at all (listing only the wired NIC)
[/LIST]

During the update I copied across the compiled modules from one kernel's modules directory tree to the other's, i.e.

```
sudo cp -p /lib/modules/2.6.28-15-generic/kernel/drivers/net/wireless/rt2870sta.ko /lib/modules/2.6.28-16-generic/kernel/drivers/net/wireless/
sudo cp -p /lib/modules/2.6.28-15-generic/updates/rt2870sta.ko /lib/modules/2.6.28-16-generic/updates/

```

Most of the other configuration seems like it should be the same between kernel versions: /etc/modules changes, /etc/Wireless config (although when it works, it works in managed mode), licd settings. So if they work for one, they should work for the other.

Most likely I've missed something to do with module setup for the new version.

Can anyone contribute some ideas? For now I am left with no choice but to use the older kernel package.

Thanks!

---

### Post by Kjeldgaard on 2009-10-28
> **bonhomme said:**
> Hi all,

I have this usb dongle working fine with jaunty, kernel  2.6.28-15-generic. However there was recently an update to 2.6.28-16-generic, which breaks it (since I have both kernels in my grub/menu.lst, I can boot the old one and it works, boot the new one, and it doesn't work, with no changes to anything in between).

When the updated kernel is booted, I get a set of diagnostics very similar to that posted by korkyboy previously:
[LIST]
[*]Linksys ID 1737:0077 shown by lsusb
[*]"ra0: ERROR while getting interface flags: No such device" returned by ifconfig ra0 inet up
[*] module not automatically loaded (doesn't appear in lsmod)
[*] if module manually loaded with modprobe, it's not used (Used by: 0 in lsmod); other commands return same errors
[*] lshw -C network does not list the wireless device at all (listing only the wired NIC)
[/LIST]

During the update I copied across the compiled modules from one kernel's modules directory tree to the other's, i.e.

```
sudo cp -p /lib/modules/2.6.28-15-generic/kernel/drivers/net/wireless/rt2870sta.ko /lib/modules/2.6.28-16-generic/kernel/drivers/net/wireless/
sudo cp -p /lib/modules/2.6.28-15-generic/updates/rt2870sta.ko /lib/modules/2.6.28-16-generic/updates/

```Most of the other configuration seems like it should be the same between kernel versions: /etc/modules changes, /etc/Wireless config (although when it works, it works in managed mode), licd settings. So if they work for one, they should work for the other.

Most likely I've missed something to do with module setup for the new version.

Can anyone contribute some ideas? For now I am left with no choice but to use the older kernel package.

Thanks!

I am not sure if I understand your problem correct but when I upgraded to 2.6.28-16 I just followed the guide from step 6. And now my wifi dingle works again.

---

### Post by bonhomme on 2009-10-31
I eventually got it working - it has to be compiled against the new kernel headers (obviously - duh!).

---

### Post by elfratysa on 2009-11-05
replace the file located in [FONT=Courier New]include/rt2870.h[/FONT] with [FONT=Courier New]rt2870.h[/FONT] from the attached [FONT=Courier New]rt2870.h.tar.gz[/FONT]

As far as I can see there is no attached rt2870.h

Am I overlooking something

grtx Elzo

---

### Post by redwark on 2009-11-05
I followed exactly the steps described by JordanL, and it works perfectly fine on my fresh install of Ubuntu 9.04 (with the green light and everything :) )

Thanks a lot to all of you !

---

### Post by bonhomme on 2009-11-07
> **elfratysa said:**
> replace the file located in [FONT=Courier New]include/rt2870.h[/FONT] with [FONT=Courier New]rt2870.h[/FONT] from the attached [FONT=Courier New]rt2870.h.tar.gz[/FONT]

As far as I can see there is no attached rt2870.h

I can see it on the bottom of the first post. The link goes to:
[http://ubuntuforums.org/attachment.php?attachmentid=113431&d=1242104367](http://ubuntuforums.org/attachment.php?attachmentid=113431&d=1242104367)

I think you have to be logged in.

---

### Post by jimbob on 2009-11-07
Does anyone know how we can go about having this driver included in the next release of Ubuntu?

It seems like there are quite a few of these RT3070 chips out there now.

I don't know much about this dkms thing but it seems to be able to take care of the VirtualBox drivers on my system automatically as kernels are upgraded.  Why wouldn't it be able to do the same with tis Ralink driver?

Should this question be asked in another forum topic?

---

### Post by Kjeldgaard on 2009-11-08
Has anyone got this working in Ubuntu 9.10? I get compile errors when I run step 6: make && make install.

I have tried the 1.4 and the 2.2 versions from Ralinks website.

Help is appreciated.

---

### Post by elfratysa on 2009-11-08
rt2870h is not present in /include. I found it in /include/chip. Dummy as I am, is this the file to be replaced and does this solution than still works?
 I downloaded 2009_0820_RT2870_Linux_STA_V2.2.0.0 as being the latest from the ralink site, seems to be the most logical thing to do, but is it really the best thing to do?

 system ubuntu 9.10 karmic koala 64 bit.
WUSB54GC V3 from Linksys Cisco.

Can anybody give me the absolute foolproof walktrough for dummy´s or give me the ndiswrapper alternative method for the Vista drivers on the DVD. I´m not a computer neard like most of you. Thought these kind of issues were something of the past when I had to install analog modems in Suse back in the nineties, but to my great surprise these kind of issues are still a part of the linux community.

Urgent HELP WANTED.

---

### Post by jimbob on 2009-11-08
Just two days ago I followed JordanL's post #98 on page 10 above and it worked immediately for me on an Ubuntu 9.04 system.  Note that he (and I) used 2009_0525_RT3070_Linux_STA_v2.1.1.0 which is the one listed for RT3070 USB on the Ralink web site.  There are a couple of minor typos and I did not have to do the last 2 steps because it worked fine without them.

I cannot speak for 9.10 or 64-bit; perhaps someone else can.

---

### Post by bombtech on 2009-11-08
YES!!  I followed the instructions in post #98 on a fresh install of 9.04 and it works!  Special thanks to Radixor, jimbob, and JordanL for your time and expertise.  That was a rough introduction to Linux/Ubuntu, but I have to admit I learned a lot.  Thanks again guys.

---

### Post by trieuvan on 2009-11-11
I followed both instructions in Radixor 's post and JordanL 's post (#98). When I followed Radixor 's, my USB adapters can recognize networks but canno connect my Ubuntu PC to the network. JordanL 's instructions make my system work in Ubuntu 9.04 (I am using WUSB54GC version 3 id: 1737:0077 too). Thanks JordanL, Radixor and jimbob. 

I made a few modifications:
1. Step3 in #98 could not be done as the link does not exist. Thus, I actually googled for the file with the same name.
2. This same instructions work for Fedora 10 too. I just need to make a small change in step 5( gedit /etc/modules/ becomes gedit/etc/modprobe.d/modprobe.conf.dist )

---

### Post by svkndv on 2009-11-11
Can anyone advise what changes needs to be done in the steps explained at #98 to make it work with 9.10?

---

### Post by kangeloux on 2009-11-11
I join the quorum in asking for 9.10 instructions ! When I do the make command get the same errors as Soulou. :popcorn:

---

### Post by kt_pie on 2009-11-11
When I tried to put in the code:

wget [http://www.ralink.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2](http://www.ralink.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2)

I get this error message: 

Resolving [www.ralink.com.tw](www.ralink.com.tw)... failed: Name or service not known. wget: unable to resolve host address 'www.ralink.com.tw'

---

### Post by jimbob on 2009-11-11
I just noticed that on the Ralink web site they have a new version of the RT3070USB driver listed with the date of 11/06/2009.  Don't know but this may be the version needed for 9.10.

I'll give it a try later today or tomorrow and let you know.

For the poster above, the web site for Ralink (linux) is [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

---

### Post by Kjeldgaard on 2009-11-11
> **jimbob said:**
> I just noticed that on the Ralink web site they have a new version of the RT3070USB driver listed with the date of 11/06/2009.  Don't know but this may be the version needed for 9.10.

I'll give it a try later today or tomorrow and let you know.

For the poster above, the web site for Ralink (linux) is [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Hi jimbob

You sound as a wise man so I have a question for you!

How do you remove all wireless drivers and settings? If it is possible.

My problem is that I first followed radixors guide in post #2. That didn't work out well. Then I followed JordanL guide in post #98 and using a patch my wireless usb worked! Then I rebooted and it has never worked since :(

I think the problem is that I have tried installing the rt2870 ver. 1.4 and the rt3070 version 2.1.1 drivers and now it is one big driver mess.

I am using Ubuntu 9.10. It all worked perfectly in 9.04.

Thanks in advance
Kjeldgaard

---

### Post by jimbob on 2009-11-11
> You sound as a wise man so I have a question for you!
Compliments will get you nowhere...  lol!

> How do you remove all wireless drivers and settings? If it is possible.
  It may be possible but if I were you, for my own peace of mind, I would back up all my personal stuff and re-install 9.10.  Since it is brand new you probably don't have too much custom stuff installed yet.

I will be trying the new 11/06/2009 package on Ralink's web site tomorrow and will post my results.

---

### Post by Kjeldgaard on 2009-11-12
> **jimbob said:**
> Compliments will get you nowhere...  lol!

I think it was a nice try though :)

  > **jimbob said:**
> 
I will be trying the new 11/06/2009 package on Ralink's web site tomorrow and will post my results.

I am looking forward to hear about your results.

My final option is to reinstall 9.10 and give it another try.

---

### Post by jimbob on 2009-11-12
Bad news.  I tried to compile both the new Ralink driver package on their web site and also the one from 5/25/2009 that had worked so well for me on 9.04 and they both failed to compile with the same error:

/home/jaspmatt/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/jaspmatt/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1510: error: ‘struct net_device’ has no member named ‘open’
/home/jaspmatt/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1511: error: ‘struct net_device’ has no member named ‘stop’
/home/jaspmatt/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1512: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/jaspmatt/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1513: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/jaspmatt/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1519: error: ‘struct net_device’ has no member named ‘get_stats’
/home/jaspmatt/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1553: error: ‘struct net_device’ has no member named ‘validate_addr’

   I will be sending this info to Ralink.  They probably have not caught up with kernel 2.6.31-14-generic yet.

---

### Post by Kjeldgaard on 2009-11-12
> **jimbob said:**
> Bad news.  I tried to compile both the new Ralink driver package on their web site and also the one from 5/25/2009 that had worked so well for me on 9.04 and they both failed to compile with the same error:

/home/jaspmatt/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/jaspmatt/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1510: error: ‘struct net_device’ has no member named ‘open’
/home/jaspmatt/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1511: error: ‘struct net_device’ has no member named ‘stop’
/home/jaspmatt/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1512: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/jaspmatt/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1513: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/jaspmatt/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1519: error: ‘struct net_device’ has no member named ‘get_stats’
/home/jaspmatt/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1553: error: ‘struct net_device’ has no member named ‘validate_addr’

   I will be sending this info to Ralink.  They probably have not caught up with kernel 2.6.31-14-generic yet.

I applied the patch from this thread: [http://www.backports.ubuntuforums.org/showthread.php?t=1285828](http://www.backports.ubuntuforums.org/showthread.php?t=1285828)

After applying the patch you should be able to compile it.

---

### Post by jimbob on 2009-11-12
Thanks for that patch, I'll give it a go later or tomorrow.  My lady is calling for me to give it up for the day and join the land of the living.

---

### Post by svkndv on 2009-11-13
I started my experiment with Ubuntu since ver. 8.04, Evey time I face an issue with my new hardware.
This time with 9.10 also no difference, I was struggling for a week to configure my WUSB54GC WLAN adapter, So far not able to configure with all the advise spread over different forums and threads.

Now only 2 solution in front of me, 
1.	Install ubuntu and live without wireless internet or pull a 10 mtr cable from one room to other.
2.	Live with Vista.

I opted for second option and again found some issue removing ubuntu, because simply deleting ubuntu partition cause crashing your boot-:KSloader. If you wish to go back to your Vista following steps(worked for me) may help you,


1. Put the Windows Vista installation disc in the disc drive, and then start the computer.
2. Press a key when you are prompted.
3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4. Click Repair your computer.
5. Click the operating system that you want to repair, and then click Next.
6. In the System Recovery Options dialog box, click Command Prompt.
7. Type 
bootrec.exe /FixMbr
bootrec.exe /fixboot


This will replace GRUB loader and retain Vista boot-loader

---

### Post by sandy8925 on 2009-11-13
It's sad to hear that you've had problems with using Ubuntu. If you tell us the version number for your WLAN adapter (i.e version 1,2,3) and whether it is a USB/PCI device maybe we can help you fix it.

Also, it's probably better to install GRUB on a separate small partition when you first install Ubuntu so that even if you do remove Ubuntu you won't face any problems.

---

### Post by Kjeldgaard on 2009-11-13
Finally it works! I am running Ubuntu 9.10, driver rt3070 ver. 2.1.1.

Here are the exact steps that I did:

**Step 1**

```
sudo -i
```**Step 2**

Download the "2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2" file. I don't know where to get it at the moment as the Ralink website has updated the 3070 drivers :( And I haven't tried the new ones.

[B]Step 3
[/B]```
tar xjf 2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2
```**Step 4**
```
cd 2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2
```**Step 5**
```
gedit os/linux/usb_main_dev.c
```and add the following line
```
{USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */
```Save and close

**Step 6**
```
gedit os/linux/config.mk
```change all the stuff to do with WPA_SUPPLICANT to y

**Step 7**
```
gedit /etc/modules
```add this line
```
alias ra0 rt3070sta
```**Step 8**
```
gedit RT2870STA.dat
```And insert your SSID, Channel, AUTHMODE, EncrypType and WPAPSK.

**Step 9**
```
cd ..
```Download the file [rt3070-2.6.31-compile.patch.gz]("http://ubuntuforums.org/attachment.php?attachmentid=132572&d=1256080042") and run
```
gunzip rt3070-2.6.31-compile.patch.gz
```and
```
patch -p0 < rt3070-2.6.31-compile.patch

```[B]Step 10
[/B]```
cd 2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2
```and
```
make && make install
```[B]
Step 11[/B]
make sure lib/modules/'uname -r'/updates folder exists or you will get a 'updates is a folder' error
```
cp -p /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt3070sta.ko /lib/modules/`uname -r`/updates/
```**Step 12**
```
depmod -a
```[B]Step 13
[/B]```
cp -f /etc/Wireless/RT3070STA/RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
```You might have to create the /etc/Wireless/RT2870STA/ folder.
[B]Step 14
[/B]```
echo "ifconfig ra0 inet up" >> /etc/init.d/rc.local
```[B]Step 15
[/B]```
gedit /etc/modprobe.d/blacklist.conf

```and add this
```
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb

```Close and save.
**Step 16**
Reboot.
[B]Step 17
[/B]```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```set managed=false to true
**Step 18**
```
sudo killall nm-system-settings
```[B]Step 19
[/B]Reboot

After these steps it worked for me.

I hope that I have corrected the typos in JordanLs guide. 

All credit goes to JordanL, lesnoland, radixor and jimbob.

---

### Post by hiren_dave85 on 2009-11-14
I have wifi adapter of i-Ball model no:  iB-WUA 108G. Ubuntu doen't detects it. Can you please help me?

---

### Post by Kjeldgaard on 2009-11-14
> **hiren_dave85 said:**
> I have wifi adapter of i-Ball model no:  iB-WUA 108G. Ubuntu doen't detects it. Can you please help me?

Insert the wifi adapter and
```
lsusb
```if this is returned
```
Bus xxx Device xxx: ID 1737:0077
```you should be able to follow my step by step guide. If not you should find the correct drivers and the procedure would be very similar I think.

---

### Post by mizunoX on 2009-11-14
> **Kjeldgaard said:**
> Step 8
gedit RT2870STA.dat
And insert your SSID, Channel, AUTHMODE, EncrypType and WPAPSK.

About the channel -- most routers use various channels and switch on the fly, don't they?  I know my Airport is set to "Automatic".
Did you set your router to just one channel and echo that in the RT2870STA.dat file?

Thanks in advance

---

### Post by Kjeldgaard on 2009-11-14
> **mizunoX said:**
> About the channel -- most routers use various channels and switch on the fly, don't they?  I know my Airport is set to "Automatic".
Did you set your router to just one channel and echo that in the RT2870STA.dat file?

Thanks in advance

I live in a building where most of my neighbours also have a wireless access point. So to minimize the interference from the other AP I used a wifi analyser to find a non occopied channel. Most of my neighbours used the channels 1-5 so I chose channel 11. I recommend that you do the same to achieve the best data rates.

When you set your router to "Automatic" I am pretty sure that it only uses one channel. How it choose the channel I don't know. Bluetooth on the other hand switches between the channels and it is called frequency hopping.

---

### Post by svkndv on 2009-11-16
> **Kjeldgaard said:**
> Finally it works! I am running Ubuntu 9.10, driver rt3070 ver. 2.1.1.



Kjeldgaard,
Your structured and easy to understand step by step instruction to configure wireless card tempted me to try ubuntu once again. Kudos to you it is working fine for me. But if you could explain few of the technicalities involved in the configuration it would be great.


1.	Can I manage this connection still with default Network Manager, like changing WPA password etc.

2.	What is the difference between ra0 and wlan0?

3.	In future if upgrade the kernel do I need to redo this steps again?

---

### Post by mizunoX on 2009-11-16
> **Kjeldgaard said:**
> 
When you set your router to "Automatic" I am pretty sure that it only uses one channel. How it choose the channel I don't know. Bluetooth on the other hand switches between the channels and it is called frequency hopping.

Oh, cool!   Learn something new every day...

Thanks!

---

### Post by Kjeldgaard on 2009-11-16
> **svkndv said:**
> 
1.    Can I manage this connection still with default Network Manager, like changing WPA password etc.
You should be able to change the WPA/WPA2 password from the Network Manager. I am not sure whether you are able to change SSID, channel and encryption mode with out redoing some of the steps in the guide.

> **svkndv said:**
> 
2.    What is the difference between ra0 and wlan0?
I don't know. I think it is just some alias, so there are probably no difference. I hope a more experienced ubuntu user can explain us the difference :)

> **svkndv said:**
> 
3.    In future if upgrade the kernel do I need to redo this steps again?
After a kernel upgrade you have to redo step 10 and 11. And you have to apply another patch.

/Kjeldgaard

---

### Post by jimbob on 2009-11-16
Thank you Kjeldgaard for the excellent procedure write-up in post #159 above.  I used that as my template to get the new 2009_1106_RT3070_Linux_STA_V2.1.1.0.bz2  driver which has now appeared on the Ralink web site to work on 9.10 Karmic.
  The only changes I had to make other than the new package name was to modify the patch itself before applying (I guess you could call this step 9a or something in the procedure) by changing 0525 to 1106 throughout.
  [B][I][COLOR="RoyalBlue"]sed -i s/0525/1106/g rt3070.2.6.31-compile.patch
[/COLOR][/I][/B]
  I should also mention that the last step, killall nm-system-settings fails with a "no process found" message; I guess they might have changed that with this release.
  Kudos to everyone involved for all the hard work; JordanL, lesnoland, radixor and Kjeldgaard.

---

### Post by Sezmeralda on 2009-11-18
To radixor, JordanL, jimbob and Kjeldgaard - wonderful, wonderful work!  I'm very new to linux & ubuntu and am enjoying the (rather steep) learning curve.

I am running 9.10 Karmic on a 64-bit system and have spent a couple of days now trying to get my WUSB54GCv3 to work.  Thanks to this thread I have finally managed.  It was Kjeldgaard's set of instructions which finally worked for me.

I found a link to the 2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2 here at [http://mahmoudimus.com/files/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2](http://mahmoudimus.com/files/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2) I don't know how long the link will work for though.

Since I am very inexperienced I would like to include some information which I hope will be helpful to others in the same boat as I:
At Step 11 Kjeldgaard refers to the file paths 
> 
/lib/modules/'uname -r'/kernel/drivers/net/wireless/rt3070sta.ko 
and 
/lib/modules/'uname -r'/updates.  
I was initially confused as to what 'uname -r' was and thought I should be replacing it with my username.
When I finally replaced 'uname -r' with the name of the only folder in /lib/modules "[COLOR=Blue]2.6.31-14-generic[/COLOR]" everything came together for me and now my wireless is working like a charm. (So far...)

Thank you again and again for the time you have put into this, for all of us.

Sez

---

### Post by radselius on 2009-11-19
Thank you Radixor and JordanL, I just got this baby working. ;)

---

### Post by hugelama on 2009-11-20
Hey guys I also have the WUSB54GC V3.

I installed the drivers for rt3070sta, and it now recognized the usb dongle.

When I iwconfig ra0 scan I get a list of all of the networks around me, but for some reason when I put it into monitor mode and try to airodump-ng I see nothing it will sit there and scan but no networks show up. 

Please help!

---

### Post by akehurst on 2009-11-21
Did you have a problem with patching rt_linux.c ? I am trying to patch  2009_1110_RT3070_Linux_STA_v2.1.2.0

---

### Post by omonos on 2009-11-22
> **Sezmeralda said:**
> 

I found a link to the 2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2 here at [http://mahmoudimus.com/files/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2](http://mahmoudimus.com/files/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2) I don't know how long the link will work for though.

Since I am very inexperienced I would like to include some information which I hope will be helpful to others in the same boat as I:
At Step 11 Kjeldgaard refers to the file paths 
I was initially confused as to what 'uname -r' was and thought I should be replacing it with my username.
When I finally replaced 'uname -r' with the name of the only folder in /lib/modules "[COLOR=Blue]2.6.31-14-generic[/COLOR]" everything came together for me and now my wireless is working like a charm. (So far...)

Thank you again and again for the time you have put into this, for all of us.

Sez

hi all,

i have been trying to do the same thing above but it does not work for me..:(

1. can't understand which rt2870.h file to replace with which.

2. make install runs but when i run the "cp" command it does not find any rt2870sta.ko file!

plz help

---

### Post by Kjeldgaard on 2009-11-22
> **akehurst said:**
> Did you have a problem with patching rt_linux.c ? I am trying to patch  2009_1110_RT3070_Linux_STA_v2.1.2.0

The patch is only working for v 2.1.1. If you want it to work with v 2.1.2 you have to do some editing. I haven't tried it but take a look at post [http://ubuntuforums.org/showpost.php?p=8330857&postcount=167](http://ubuntuforums.org/showpost.php?p=8330857&postcount=167) for guidance.

---

### Post by Kjeldgaard on 2009-11-22
> **omonos said:**
> hi all,

i have been trying to do the same thing above but it does not work for me..:(

1. can't understand which rt2870.h file to replace with which.

2. make install runs but when i run the "cp" command it does not find any rt2870sta.ko file!

plz help

1: Which step-by-step guide are you using? Because you don't have to replace a rt2870sta.h file.

2: Is it when you perform step 13 you get the error?

---

### Post by AFI420 on 2009-11-22
First off Im really new using Linux/ubuntu. Ive been trying to get my WUSB54GC working for about a week. Ive used ra linux drivers, ndiswrapper, wicd. None worked.

The closest point I got was I beleive with ndiswrapper, I could actually get my network manager to scan for AP's, but couldnt connect. Now ive followed a mix of klejard & jordans procedure using the newest driver from RA the  2009_1110. The release notes say that it was updated to work with the newest kernal, so i skipped the part about the compile patch and had no errors when making the driver, but still cant connect. It just doesnt look like the system realizes that a USB device could actually be a wireless adapter.

Ive learned quite a bit over the last week about linux, more than I thought I would, but Id like to take a break and just be able to browse the internet on ubuntu. Ive spent about 3 hours a day trying to get this to work.


I will post some of my outputs when I get home; currently at work

Ive also removed network-manager and only have wicd installed. How do I go back if I need to?

---

### Post by AFI420 on 2009-11-22
after reading through this a few times. I think I will try to reinstall NM then run through this procedure patching the newest file available and trying again. Is there any updates out there that might fix this problem that I can access if I use a wired connection?

---

### Post by radixor on 2009-11-22
Judging from the amount of trouble that people are having, would everyone feel more comfortable if I wrote a small python script to do this for you?

I don't mind, it'll be pretty easy.

---

### Post by AFI420 on 2009-11-22
please do. I got my adapter to be recognized and be able to scan for networks after running a wired update, but when getting to connecting to the router it hangs at obtaining and IP or auth. so I reinstalled OS and now i cant see the adapter again. all I did before was run updates.


UPDATE: ok, i used kledjards procedure from page 16 except used the most recent (11/10/09) driver and left out the patching part and the last step of killing NM because Im using wicd. THANKS EVERYONE!

---

### Post by sushrut91 on 2009-11-23
Thanks for help  everyone especially to Jimbob and JordanL

I followed the procedure mentioned on Post 98 with the New Ralink Driver on Ubuntu 9.10
It works!!

No need for new patches.
Please use the attached file with the procedure on Post #98

Hope you suceed.

Please Note: *On upgrading to a new kernel version make sure you run Step#7 : *after changing to the directory of the driver in your root.
make && make install

---

### Post by flhtguy on 2009-11-26
Still not having much luck here. 
1) 2.6.31-15-generic
2) No ra0 but I do have a wlan1
3) No errors when compiling
4) No lights on dongle
5) Have replaced NM with WiCD

Anymore suggestions will be greatly appreciated

Happy Holidays
Jim

---

### Post by titopagan on 2009-11-27
@radixor

I am very interested on the script you offered to write.  Would it be possible for you to  upload it.   Thanks

---

### Post by b k on 2009-12-01
Hi, I am new to Ubuntu but have been doing a lot of reading up on this forum.
This is my first posting so if I am doing anything improper, please let me know.

All credit goes to everyone who has posted previously here which has enabled me to get the Wusb54gc v3 working.

I followed all the steps below **initially** with fresh install and  **2.6.31-14-generic** kernel and **NetworkManager**. The usb adapter worked well at the end of the steps.

However after using Update Manager and installing the updates with 2.6.31-15-generic kernel, the adapter failed to work again.

I repeated the steps (skipping some and slightly modifying others) replacing the 2.6.31-14-generic with 2.6.31-15-generic at the appropriate steps and the adapter worked well again.

Using Update Manager and installing the updates with 2.6.31-16-generic kernel, caused the adapter to stop working again.

Repeating the steps (skipping some and slightly modifying others) , replacing the 2.6.31-15-generic with 2.6.31-16-generic at the appropriate steps resulted in the adapter working well again.

I have attached a .txt file containing all the code and steps posted here and also the required driver from ralink.com.tw


Hope this post helps those who are still trying to get this adapter to work well.

Operating system: 
 
- fresh install of Ubuntu 9.10 desktop 32 bit version with 2.6.31-14-generic kernel.
- if you are running Ubuntu 9.10 with a higher generic kernel number please see Special Notes below. 
 
 
**Before starting ****:**
- Open a Terminal window and type uname -r to **find out which kernel number you are using.**
- Follow the appropriate set of Steps below
          
- download 2009_1110_RT3070_Linux_STA_v2[1].1.2.0.tar.bz2 file
 (from ralink.com.tw) - (*skip if you have done so previously*).
     
- place file in /home/user/Downloads
- (if you have partitioned your hardisk differently, then you need to make the necessary adjustments as the directories and file locations will be different.) - (*skip if you have done so previously*).

- Navigate to the downloaded file and double click (*skip if you have done so previously*).
 
     
 
Suggestion: 
 
- Copy these instructions which is in a .txt file somewhere convenient, open the file so that      
- you can copy and paste the code/commands to a Terminal. 

- precede your code with sudo if permission denied message pops up at any stage. 
 

Go to 
Applications, Accessories, Terminal    to open a terminal window


 
 
 
Step 1 
 
      Code: 
sudo -i 
 
 



Step 2 
 
      Code: 
cd /home/user/Downloads 

 
 
Step 3 
 
      Code: 
tar xjf 2009_1110_RT3070_Linux_STA_v2[1].1.2.0.tar.bz2


 
 
 
Step 4 
 
      Code: 
cd /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0


 
 
 
Step 5 
 
      Code: 
gedit os/linux/usb_main_dev.c       and add the following line 
 
      Code: 
{USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */

Save and close 

 
 
Step 6 
 
      Code: 
gedit os/linux/config.mk       change all the stuff to do with WPA_SUPPLICANT to y 

 
Save and close 
         
 
Step 7 
 
      Code: 
gedit /etc/modules   add this line 
 
      Code: 
alias ra0 rt3070sta 
 
Save and close

 
 
 
Step 8 
 
      Code: 
gedit RT2870STA.dat    and insert your SSID, Channel, AUTHMODE, EncrypType and WPAPSK 
 
 
For info :  
- I only entered my SSID; selected WPA2PSK for 4.) ;TKIP for 5.) and left the rest alone 
 

- 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infra (ie infrastructure) 

- 2.) set Channel to "0" for auto-select on Infra mode
 
- 3.) set SSID for connecting to your Accss-point  

- 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE" 

- 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES" 

 
 

Step 9 
 
      Code: 
cd /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0       and 
 
      Code: 
make && make install     


 
 
 
Step 10
 
 
      Code:
 
mkdir /lib/modules/2.6.31-14-generic/updates 
 
  


Step 11
 
 
      Code: 
cp -p /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/rt3070sta.ko /lib/modules/2.6.31-14-generic/updates/


 
 
 
Step 12 
 
      Code: 
depmod -a


 
 
 
Step 13
 
 
      Code: 
mkdir /etc/Wireless/RT2870STA
 
 
      Code: 
cp -f /etc/Wireless/RT3070STA/RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat 
 
 


Step 14 
 
      Code: 
echo "ifconfig ra0 inet up" >> /etc/init.d/rc.local


 
 
 
Step 15 
 
      Code: 
gedit /etc/modprobe.d/blacklist.conf      and add this 
 
      Code: 
blacklist rt2x00usb 
blacklist rt2x00lib 
blacklist rt2800usb          Save and close 
 
 


Step 16 
      Reboot 
 
 
Step 17 
 
      Code: 
sudo gedit /etc/NetworkManager/nm-system-settings.conf        set managed=false to true 
 
 
 

Step 18 
      Reboot


All credit goes to Kjeldgaard, JordanL, lesnoland, radixor jimbob and others on this forum

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



SPECIAL NOTES:
Once you use your Update Manager to update your Kernel to 2.6.31-15-generic kernel, the wireless adapter fails to work again.

Follow the steps below (precede your code with sudo if permission denied message pops up).
Some of the steps may be unnecessary but they worked for me.

Go to 
Applications, Accessories, Terminal    to open a terminal window


Step 1 
 
      Code: 
sudo -i

Skip Steps 2 and 3


Step 4 
 
      Code: 
cd /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0


 
 
 
Step 5 
 
      Code: 
gedit os/linux/usb_main_dev.c       and add the following line 
 
      Code: 
{USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */

Save and close 

 
 
Step 6 
 
      Code: 
gedit os/linux/config.mk       change all the stuff to do with WPA_SUPPLICANT to y 

 
Save and close 
         
 
Step 7 
 
      Code: 
gedit /etc/modules   add this line 
 
      Code: 
alias ra0 rt3070sta 
 
Save and close

 
 
 
Step 8 
 
      Code: 
gedit RT2870STA.dat    and insert your SSID, Channel, AUTHMODE, EncrypType and WPAPSK 
 
 
For info :  
- I only entered my SSID; selected WPA2PSK for 4.) ;TKIP for 5.) and left the rest alone 
 

- 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infra (ie infrastructure) 

- 2.) set Channel to "0" for auto-select on Infra mode
 
- 3.) set SSID for connecting to your Accss-point  

- 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE" 

- 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES" 

 
 

Step 9 
 
      Code: 
cd /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0       and 
 
      Code: 
make && make install     


 
 
 
Step 10
 
 
      Code:
 
mkdir /lib/modules/2.6.31-15-generic/updates 
 
  


Step 11
 
 
      Code: 
cp -p /lib/modules/2.6.31-15-generic/kernel/drivers/net/wireless/rt3070sta.ko /lib/modules/2.6.31-15-generic/updates/


 
 
 
Step 12 
 
      Code: 
depmod -a


 
 
 
Step 13  

      Code: 
mkdir /etc/Wireless/RT2870STA 
 
      Code: 
cp -f /etc/Wireless/RT3070STA/RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat 
 
 


Step 14 
 
      Code: 
echo "ifconfig ra0 inet up" >> /etc/init.d/rc.local


 
 
 
Step 15 
 
      Code: 
gedit /etc/modprobe.d/blacklist.conf      and add this 
 
      Code: 
blacklist rt2x00usb 
blacklist rt2x00lib 
blacklist rt2800usb          Save and close 
 
 


Step 16 
      Reboot


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

SPECIAL NOTES:
Once you use your Update Manager to update your Kernel to 2.6.31-16-generic kernel, the wireless adapter fails to work again.

Follow the steps below (precede your code with sudo if permission denied message pops up).
Some of the steps may be unnecessary but they worked for me.

Go to 
Applications, Accessories, Terminal    to open a terminal window


Step 1 
 
      Code: 
sudo -i


Skip Steps 2 and 3


Step 4 
 
      Code: 
cd /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0


 
Step 5 
 
      Code: 
gedit os/linux/usb_main_dev.c       and add the following line 
 
      Code: 
{USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */

Save and close 

 
 
Step 6 
 
      Code: 
gedit os/linux/config.mk       change all the stuff to do with WPA_SUPPLICANT to y 

 
Save and close 
         
 
Step 7 
 
      Code: 
gedit /etc/modules   add this line 
 
      Code: 
alias ra0 rt3070sta 
 
Save and close

 
 
 
Step 8 
 
      Code: 
gedit RT2870STA.dat    and insert your SSID, Channel, AUTHMODE, EncrypType and WPAPSK 
 
 
For info :  
- I only entered my SSID; selected WPA2PSK for 4.) ;TKIP for 5.) and left the rest alone 
 

- 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infra (ie infrastructure) 

- 2.) set Channel to "0" for auto-select on Infra mode
 
- 3.) set SSID for connecting to your Accss-point  

- 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE" 

- 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES" 

 
 

Step 9 
 
      Code: 
cd /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0       and 
 
      Code: 
make && make install     


 
 
 
Step 10
 
 
      Code:
 
mkdir /lib/modules/2.6.31-16-generic/updates 
 
  


Step 11
 
 
      Code: 
cp -p /lib/modules/2.6.31-16-generic/kernel/drivers/net/wireless/rt3070sta.ko /lib/modules/2.6.31-16-generic/updates/


 
 
 
Step 12 
 
      Code: 
depmod -a


 
 
 
Step 13  

      Code: 
mkdir /etc/Wireless/RT2870STA 
 
      Code: 
cp -f /etc/Wireless/RT3070STA/RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat 
 
 


Step 14 
 
      Code: 
echo "ifconfig ra0 inet up" >> /etc/init.d/rc.local


 
 
 
Step 15 
 
      Code: 
gedit /etc/modprobe.d/blacklist.conf      and add this 
 
      Code: 
blacklist rt2x00usb 
blacklist rt2x00lib 
blacklist rt2800usb          Save and close 
 
 


Step 16 
      Reboot

---

### Post by grief -l on 2009-12-01
Hi everybody, I'm new here and new to linux and ubuntu so thanks to all for the tuts here!
 
Unfortunately, I get to:
 
```
make && make install 
```
 
and right at the end of that long stream of jargon it says ERROR 2. Obviously nothing after that works because it can' find files or directories and suchlike. Not sure if I should just do the make && makefile again or what? I feel like I'm playing Packman every time I have to goto the console. Hope I haven't chewed up too much code!
 
Gabe

---

### Post by wolfen3 on 2009-12-03
> **grief -l said:**
> Hi everybody, I'm new here and new to linux and ubuntu so thanks to all for the tuts here!
 
Unfortunately, I get to:
 
```
make && make install 
```and right at the end of that long stream of jargon it says ERROR 2. Obviously nothing after that works because it can' find files or directories and suchlike. Not sure if I should just do the make && makefile again or what? I feel like I'm playing Packman every time I have to goto the console. Hope I haven't chewed up too much code!
 
Gabe

I have the same error

---

### Post by jonesy10tech on 2009-12-06
Thanks B K and the rest for the good info. Worked flawlessly!

---

### Post by Kojans on 2009-12-06
Thanks B K, and all others in this post! I printed your instructions, going to try next week.
I had some difficulty finding the right place to download the driver; it seems that Ralink quite often changes their websites...
I found the '2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2' file on: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) .

---

### Post by b k on 2009-12-06
> **Kojans said:**
> Thanks B K, and all others in this post! I printed your instructions, going to try next week.

The easiest way is to copy the attached .txt file (which contain the instructions and code) at the end of my post to your Ubuntu machine via a flash pendrive and open the file with a basic text editor (say on workspace "Desk 2").

Switch to workspace "Desk 1" and open a Terminal window.

By switching between Desk 2 and Desk 1, you can copy and paste the code/commands for each step to the Terminal window and execute the steps one at a time.

This will save you a lot of work and typing errors.
Typing the code yourself should be done only as a last resort.

If you do not trust what is in the attached .txt file, you can get the same by saving my post as a .txt file yourself.

Good luck!

---

### Post by titopagan on 2009-12-07
@ BK
Great instructions worked for me.  Just one question How can you connect to other networks?

---

### Post by b k on 2009-12-07
> **titopagan said:**
> @ BK
Just one question How can you connect to other networks?

How to connect to another wireless network using NetworkManager:

- right click on wireless connection icon (top right of your desktop).

- right click on the name of the wireless network you wish to connect to.

- enter the password or encryption key of the network (get this from the network administrator).

- click connect.

This should work if NetworkManager is functioning normally (i.e with the workaround to install the Ralink driver for the Wusb54gc v3 usb adapter).

Hope it works for you.

---

### Post by b k on 2009-12-07
> **grief -l said:**
> 
 
Unfortunately, I get to:
 
```
make && make install 
```and right at the end of that long stream of jargon it says ERROR 2. Obviously nothing after that works because it can' find files or directories and suchlike. Not sure if I should just do the make && makefile again or what?
 
Gabe



I may have left out some info in my original #182.

I have edited the same post and provided more detailed info.

Please read post #182 and also #187 and if you feel like it, give it another go.

Good luck!

---

### Post by grief -l on 2009-12-08
Thanks for all your help and the trouble you've gone to but I'm not going to hassle with this anymore. I have dual boot with XP and it works there so I'll just wait for a bugfix release or get another dongle. 
 
Your helps appreciated though!

---

### Post by flhtguy on 2009-12-08
Thanks to all for the help in getting this to work. For those still having issues with compiling the module remember to make yourself **ROOT** with the **sudo** command. And just to be on the safe side use **sudo** before each of the commands.
The Best to All

---

### Post by titopagan on 2009-12-08
This topic should be a sticky.

Great job B K.

---

### Post by Kojans on 2009-12-08
Hi B K and others,

The printed instructions worked for me! I'am writing this on my laptop, connected via the Linksys-adaptor! I updated before to kernel 2.6.31-15-generic, so I used this part of the text. I wrote down some comments while working through the steps; my plan is to convert the text to HTML and put it on my webserver (supposed that it's o.k. to you, BK?) . I'll post it here when I've had the time to work this out.

Thanks again!!

---

### Post by illuminaris on 2009-12-08
Everything goes fine until I get to step 6. This is the feedback I got in terminal after copying and pasting the command.

> root@Illuminaris:/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0# make && make install
make -C tools
make[1]: Entering directory `/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.31-16-generic/build SUBDIRS=/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  CC [M]  /home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.o
/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c: In function &#8216;RTMPReadParametersHook&#8217;:
/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:928: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsuid&#8217;
/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:929: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsgid&#8217;
/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:930: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsuid&#8217;
/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:930: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsgid&#8217;
/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:1593: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsuid&#8217;
/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:1594: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsgid&#8217;
make[2]: *** [/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.o] Error 1
make[1]: *** [_module_/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [LINUX] Error 2


I tried to go ahead with Step 7 anyways and did a mkdir /lib/modules/`uname -r`/updates/ but terminal says folder already exists. So I moved to the next step and got this feedback.

> root@Illuminaris:/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0# cp -p /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2870sta.ko /lib/modules/`uname -r`/updates/
cp: cannot stat `/lib/modules/2.6.31-16-generic/kernel/drivers/net/wireless/rt2870sta.ko': No such file or directory


Any advice on how to proceed? I've been at this for days now with absolutely no luck.... :(

*EDIT: Ok, I figured out that you are supposed to use the feedback from uname -r in place of `uname -r`. I did that, but I still do not have a rt2870sta.ko file anywhere on my computer. Where should I find this and how do I install it?
Also, for the steps 5 and 6, should I be CD'd into the 2008_0925_RT2870_Linux_STA_v1.4.0.0 folder when I enter those commands, because that's what I did.

---

### Post by b k on 2009-12-08
Hi. I was wondering which postcount #xxx number you are following (your post is postcont #195).
 
I am new to Ubuntu just like many others here but would like to offer some suggestions:
 
1.  There are currently 4 attachments to this thread - make sure you download & use the correct ones for whichever postcount number you are following.
 
2.  Depending on how you partition your hard disk during Ubuntu installation and where you download the required driver, you may need to make minor changes to the instructions as your directory structure may be different.
 
3.  In the Terminal window always make sure that you are in the correct part of the directory before executing the code/command. 
     Sometimes, in between steps people close the Terminal window to do other things but when they open a Terminal window again and try to execute the next step, they get error messages since they are now in a different part of the directory.
 
4.  If 'permission denied' message pops up, precede your command with **sudo**
 
5**.**  You may have to use **mkdir  **tocreate the folder if no such file or directory message pops up.
 
Perhaps you may like to give a try to the procedure which I have posted in #182 and #187 if all else fails.
 
Don't give up, you will succed eventually - I did (with the hard work done by other earlier posters).

---

### Post by illuminaris on 2009-12-08
B K, Thank you so much for your help. You're very kind. Here is my updated status:

I started using your guide at post #182. I was originally using the primary guide, I think it's post #2. I'm using the attachment from there, which is the rt2870 file. I changed names where necessary and your guide got me much further. There were a lot more productive looking lines in terminal when I got to the make && make install command this time, but ultimately it ended the same way. I get this feedback toward the end: 

> /home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:928: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsuid&#8217;
/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:929: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsgid&#8217;
/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:930: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsuid&#8217;
/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:930: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsgid&#8217;
/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:1593: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsuid&#8217;
/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:1594: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsgid&#8217;
make[2]: *** [/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.o] Error 1
make[1]: *** [_module_/home/illuminaris/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [LINUX] Error 2


And then when I try to copy the .ko file in the next step it says it doesn't exist. Any ideas?

*EDIT: I'd be willing to start fresh with your guide, but I don't know how to undo everything from the first guide and delete the 2870 drivers.

---

### Post by b k on 2009-12-08
Hi again, I think it is a bad idea to use instructions in #182 but with other drivers.
 
If your Ubuntu machine is not your bread and butter one, I suggest you just repeat everything in **#182** but with **those drivers mentioned in that post**.
Remember to use cut and paste to get the commands into the Terminal window rather than manually typing (which easily leads to human typo errors).
 
I have basically repeated those steps (3 times) upgrading from kernels 2.6.31-14-generic thru' kernels 2.6.31-16-generic without any problem. Ubuntu is robust or I have been very lucky!
 
Be reminded that I am new to Ubuntu OS.
 
However as long as you are prepared for that complete reinstall of Ubuntu OS possibility, be brave
and proceed.
 
Keeping my fingers cross for you. Good luck.

---

### Post by illuminaris on 2009-12-08
I don't know what's wrong with me, then. Because I've tried going back and repeating the steps in the guide and it doesn't seem to be working. Oh well. I guess I'll just have to keep searching for solutions. Thanks for your help.

---

### Post by illuminaris on 2009-12-09
Ok, now I have a new issue that I need help with..... :(
I went through your guide, start to finish, and everything seemed to work fine. No errors that I noticed along the way or anything like that. I restarted, left my wireless card in and unplugged my ethernet cord. Upon rebooting, the wireless card did not light up nor did it connect to the internet. So I tried unplugging it and plugging it back in. Still nothing. I tried plugging the hard line in, nothing. I tried unplugging the wireless USB and leaving the hardline. Nothing. Now I am on my fiancee's windows PC making this post because neither the hard line nor the USB will work. How do these things happen?.... Can you help me fix it?

*EDIT: P.S. I used your drivers attached to post #182.

*UPDATE: I finally got my hardline working on my Ubuntu machine. I also went back and found a line I had missed in the original instructions: sudo gedit /etc/NetworkManager/nm-system-settings.conf        set managed=false to true
After doing that and rebooting, then plugging my hardline back in, the hardline works, but still no light on the wireless card. When I run:
lsusb
I get this line: Bus 001 Device 007: ID 1737:0077 Linksys
So I know it's there, and I know it recognizes it. Why it won't light up or work after all these attempts I have no idea.

*UPDATE2: Or so I thought I got the hardline working. Back on the fiancee's windows comp..... it seems like everything is going nuts on Ubuntu. Somehow I can get update manager to download updates, and yet nothing will work in firefox. Earlier, just before I made this update, websites would work for 10 seconds and then not work for 10 seconds on and off. It did that for about 5 minutes and then just died.

---

### Post by flhtguy on 2009-12-09
Have you tried **sudo /etc/init.d/networking restart **and look at /var/log/syslog to see if anything in there points to what your issue could be. You could open two terminals and in one run the networking command and in the other do this:
**sudo tail -f /var/log/syslog. **
I hope this might help to shed some light on what your problem could be.

---

### Post by illuminaris on 2009-12-09
Thanks for the suggestion flhtguy, here are the results:

I ran both commands you suggested. The restart gave me a warning: ifup -a is disabled in favour of NetworkManager.
 Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf

The tail gave a ton of feedback which I do not have the luxury of posting here because I can't access the internet on my Ubuntu machine. I'll do my best to re-type/shorthand it:

> Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.11
Withdrawing address record for 192.168.1.11 on eth0
ekge eth1: disabling interface
(eth1): carrier now OFF (device state 8 deferring action for 4 seconds)
Interface eth1.IPv4 no longer relevant for mDNS
Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.12
Withdrawing address record on eth1
Withdrawing address record for 192.168.1.12 on eth1
(eth1): device state change: 8 -> 2 (reason 40)
(eth1): deactivating device (reason: 40)
Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1

I don't know what any of that means. Any tips?

*EDIT: Note, I did not have my wireless adapter plugged in when I performed these commands. If you'd like me to re-do it with the USB adapter plugged in, I will be happy to.

*EDIT2: Oh yeah, and I ran the tail before I ran the restart. Before the restart it brought up a bunch of lines that looked like this:

> 
kernel: [  937.446423] Unknown OutputIN= OUT=eth0 SRC=192.168.1.12 DST=192.168.1.255 LEN=263 TOS=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=243


*EDIT3: I just plugged my wireless adapter in and unplugged my hardline. The tail gave me this feedback:

> usb 1-4: new high speed USB device using ehci_hcd and address 3
usb 1-4: configuration #1 chosen from 1 choice
Disabling lock debugging due to kernel taint
ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
usbcore: registered new interface driver ndiswrapper

No extra feedback after I restarted network again.

---

### Post by flhtguy on 2009-12-09
When I had problems with Network Manager I switched to WICD. If you have your install CD still add it as as source and install it. I use it and have had no problems at all.

Once again I hope that this helps a bit. 

Jim

---

### Post by dhom on 2009-12-09
> **flhtguy said:**
> When I had problems with Network Manager I switched to WICD. If you have your install CD still add it as as source and install it. I use it and have had no problems at all.

Once again I hope that this helps a bit. 

Jim
  sorry if this is a noob question, but how do you add the CD as a source? im kinda brand new to linux and im stuck at this point
also, how do i change my managed=false to true?

---

### Post by flhtguy on 2009-12-09
I should've noticed this before. If you got your wireless stick running with the steps in this thread why are you using **NDISWRAPPER**? I would recommend that you uninstall it and go through the steps again.

---

### Post by flhtguy on 2009-12-09
Edit your** /etc/apt/sources.list**. At the top of the list you should see the following entry:
You can use the following command from a terminal:
**sudo gedit /etc/apt/sources.list **or whatever text editor you are used to using. I prefer **vim.**
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted.

Uncomment (Remove the # sign). After doing this run
**sudu apt-get update. **This will update the apt database with your CD ROM as a source. Then run
[B]sudo apt-get install wicd.
[/B]Once again I hope this helps.
Jim

---

### Post by illuminaris on 2009-12-09
flhtguy, I tried uninstalling ndiswrapper and going back through all the commands in the guide. Nothing worked. Still no light on the adapter, still no internet.

I had ndiswrapper installed from a previous guide I tried to use, I didn't install it after the guide from post #182. Also, I haven't gotten the adapter to work even once yet, using any of the 4 guides I've looked up.

Anything else I can try?

---

### Post by b k on 2009-12-09
Well at least one of the output lines 'Device 007: ID 1737:0077' identifies your adapter correctly

I have read the posts on page 21 and suggests that you remove ndiswrapper first (as I believe that you only need to use it when you are actually using the windows driver for your wireless adaptar). Reboot and see what happens.

AFAIK the instructions in #182 is meant to be used with the NetworkManager.
Anyway what I have read in this forum is that you should normally uninstall NetworkManager if you are installing WICD.

Perhaps you should leave your wired connection unplugged temporarily whilst you are trying to get your wireless working.

If at the end you need to execute 'plan Z' ................ a reinstall of the OS, perhaps you can have 3 partitions - one root, one home, and one SWAP
This will then enable you to follow the same exact steps in #182 without any modifications to the directory & commands.

We are all rooting for you - good luck!

---

### Post by illuminaris on 2009-12-09
B K, unfortunately I already tried uninstalling ndiswrapper and going back through all the steps in the #182 guide. To no avail.

Is there some way I can undo what I did in the #2 guide? Maybe they are conflicting somehow.

If I do decide to install a fresh OS, does that mean I'll have to upload all my personal stuff to a USB drive or can I just reinstall the OS without having to lose any of my files? Sorry I suck at all this, you'd think I'd be better considering I've been using Ubuntu for like 2 years. I just don't understand it, but I still like it better than Windows or Mac.

---

### Post by flhtguy on 2009-12-10
As far as the **make **&** make install** errors are concerned I had the same issue when I started trying to get this USB device to work weeks ago. I noticed that the following line
that you put into os/linux/usb_main_dec.c was missing a comma. After I fixed this it is worked. I don't know if this was the issue.[B]
{USB_DEVICE(0x1737,0x0077)}[COLOR=Red],[/COLOR] /* Linksys WUSB54GC */[/B]
Make sure that the **comma **that is red is there before compiling the module. 

If I understood BK correctly you can back up all of the data that you need and do a fresh re-install of the O.S. I did this and eventually got it working. 
In the Cheering Section for You
Jim

---

### Post by illuminaris on 2009-12-10
fhltguy, I double checked that the comma was in there, which it is, but it brought up a new question. When I go to edit the usb_main_dev.c file it doesn't have any text in it except my entry of the USB device code from the guide. Should there be anything else in that file? Or just what I was told to put in there? Also, just to double check,  which folder should I be in when I run that gedit command?

Thank you guys so much. You're so nice and helpful, why I love the Ubuntu community. =)

---

### Post by willrockformilk on 2009-12-10
First of all to everyone who is helping people in this thread. Thank You. You are absolutely right when you say without this, linux would be no better than microsoft. 

Now. I have read throughout this thread and gotten the driver installed using #2 and the driver works like a charm. However i seem to be having the same problem as everyone else in that it wont authenticate. 

If someone could help me that would be great. 

dmesg while trying to connect: 

```
[57051.040754] DRS: unkown mode,default use 11N 1S AP 
[57051.040762] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57058.098681] DRS: unkown mode,default use 11N 1S AP 
[57058.098688] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57077.077724] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[57077.078055] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[57077.143413] DRS: unkown mode,default use 11N 1S AP 
[57077.143421] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57084.209716] DRS: unkown mode,default use 11N 1S AP 
[57084.209724] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57102.094656] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[57102.094969] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[57102.133811] DRS: unkown mode,default use 11N 1S AP 
[57102.133820] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57110.118202] DRS: unkown mode,default use 11N 1S AP 
[57110.118210] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57121.927143] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[57121.927490] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[57121.995815] DRS: unkown mode,default use 11N 1S AP 
[57121.995824] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57129.983489] DRS: unkown mode,default use 11N 1S AP 
[57129.983497] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57146.943613] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[57146.943925] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[57146.983218] DRS: unkown mode,default use 11N 1S AP 
[57146.983226] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57154.970606] DRS: unkown mode,default use 11N 1S AP 
[57154.970615] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57171.956158] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[57171.956436] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[57171.974865] DRS: unkown mode,default use 11N 1S AP 
[57171.974874] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57260.454380] Terminate the TimerQThr_pid=2724!
[57260.454468] Terminate the MLMEThr_pid=2722!
[57260.454489] Terminate the RTUSBCmdThr_pid=2723!
[57260.466204] ---> RTMPFreeTxRxRingMemory
[57260.466253] <--- ReleaseAdapter
[57312.817008] <-- RTMPAllocTxRxRingMemory, Status=0
[57312.827235] -->RTUSBVenderReset
[57312.827356] <--RTUSBVenderReset
[57313.206775] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[57313.206814] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[57313.206851] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[57313.206890] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[57313.207996] 1. Phy Mode = 5
[57313.208019] 2. Phy Mode = 5
[57313.237698] RTMPSetPhyMode: channel is out of range, use first channel=1 
[57313.254793] 3. Phy Mode = 9
[57313.262917] MCS Set = ff 00 00 00 01
[57313.335407] <==== RTMPInitialize, Status=0
[57313.337149] 0x1300 = 00064300
[57323.832021] ra0: no IPv6 routers present
[57364.086241] DRS: unkown mode,default use 11N 1S AP 
[57364.086249] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57369.095725] DRS: unkown mode,default use 11N 1S AP 
[57369.095734] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57376.162564] DRS: unkown mode,default use 11N 1S AP 
[57376.162573] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57386.197954] DRS: unkown mode,default use 11N 1S AP 
[57386.197963] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57396.235271] DRS: unkown mode,default use 11N 1S AP 
[57396.235278] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57407.076076] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[57409.244310] DRS: unkown mode,default use 11N 1S AP 
[57409.244318] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57419.274477] DRS: unkown mode,default use 11N 1S AP 
[57419.274484] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57429.312155] DRS: unkown mode,default use 11N 1S AP 
[57429.312163] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57439.346729] DRS: unkown mode,default use 11N 1S AP 
[57439.346738] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57449.392002] DRS: unkown mode,default use 11N 1S AP 
[57449.392028] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57459.519161] DRS: unkown mode,default use 11N 1S AP 
[57459.519170] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57469.558213] DRS: unkown mode,default use 11N 1S AP 
[57469.558222] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57479.692122] DRS: unkown mode,default use 11N 1S AP 
[57479.692130] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57489.730421] DRS: unkown mode,default use 11N 1S AP 
[57489.730430] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57499.764472] DRS: unkown mode,default use 11N 1S AP 
[57499.764481] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57508.991947] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[57508.992295] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[57509.088238] DRS: unkown mode,default use 11N 1S AP 
[57509.088258] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57516.053965] DRS: unkown mode,default use 11N 1S AP 
[57516.053974] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57527.077801] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[57527.078120] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[57527.108378] DRS: unkown mode,default use 11N 1S AP 
[57527.108386] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57534.174275] DRS: unkown mode,default use 11N 1S AP 
[57534.174283] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57552.095871] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[57552.096202] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[57552.196719] DRS: unkown mode,default use 11N 1S AP 
[57552.196727] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57559.260772] DRS: unkown mode,default use 11N 1S AP 
[57559.260781] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57647.077385] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[57767.076157] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[57887.072077] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[57903.172504] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[57903.188874] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[57903.235781] DRS: unkown mode,default use 11N 1S AP 
[57903.235789] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57910.302485] DRS: unkown mode,default use 11N 1S AP 
[57910.302493] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57928.221159] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[57928.221480] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[57928.327903] DRS: unkown mode,default use 11N 1S AP 
[57928.327912] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57935.393609] DRS: unkown mode,default use 11N 1S AP 
[57935.393618] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57953.233883] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[57953.234216] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[57953.312297] DRS: unkown mode,default use 11N 1S AP 
[57953.312306] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[57960.378601] DRS: unkown mode,default use 11N 1S AP 
[57960.378609] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[58007.077455] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[58121.548774] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[58121.549081] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[58121.577182] DRS: unkown mode,default use 11N 1S AP 
[58121.577190] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[58137.076062] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[58137.076383] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[58137.127922] DRS: unkown mode,default use 11N 1S AP 
[58137.127931] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[58144.193512] DRS: unkown mode,default use 11N 1S AP 
[58144.193520] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[58162.090905] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[58162.091240] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[58162.115858] DRS: unkown mode,default use 11N 1S AP 
[58162.115866] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[58169.181148] DRS: unkown mode,default use 11N 1S AP 
[58169.181158] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[58247.093327] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[58367.089569] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[58487.074904] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[58607.092172] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[58727.096260] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[58763.641231] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[58763.682895] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[58763.741317] DRS: unkown mode,default use 11N 1S AP 
[58763.741325] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
```tail -100 /var/log/syslog

```
Dec 10 08:34:59 laroom-desktop NetworkManager: <info>  (ra0): device state change: 6 -> 9 
Dec 10 08:34:59 laroom-desktop NetworkManager: <info>  Activation (ra0) failed for access point (3conf) 
Dec 10 08:34:59 laroom-desktop NetworkManager: <info>  Marking connection 'Auto 3conf' invalid. 
Dec 10 08:34:59 laroom-desktop NetworkManager: <info>  Activation (ra0) failed. 
Dec 10 08:34:59 laroom-desktop NetworkManager: <info>  (ra0): device state change: 9 -> 3 
Dec 10 08:34:59 laroom-desktop NetworkManager: <info>  (ra0): deactivating device (reason: 0). 
Dec 10 08:34:59 laroom-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Dec 10 08:36:07 laroom-desktop kernel: [58247.093327] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
Dec 10 08:38:07 laroom-desktop kernel: [58367.089569] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
Dec 10 08:40:02 laroom-desktop /USR/SBIN/CRON[30190]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 10 08:40:07 laroom-desktop kernel: [58487.074904] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
Dec 10 08:41:20 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
Dec 10 08:41:25 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
Dec 10 08:41:31 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
Dec 10 08:41:42 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
Dec 10 08:41:54 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
Dec 10 08:42:06 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
Dec 10 08:42:07 laroom-desktop kernel: [58607.092172] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
Dec 10 08:42:21 laroom-desktop dhclient: No DHCPOFFERS received.
Dec 10 08:42:21 laroom-desktop dhclient: No working leases in persistent database - sleeping.
Dec 10 08:44:07 laroom-desktop kernel: [58727.096260] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  Activation (ra0) starting connection 'Auto 3conf' 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  (ra0): device state change: 3 -> 4 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) started... 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) complete. 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) starting... 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  (ra0): device state change: 4 -> 5 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  Activation (ra0/wireless): access point 'Auto 3conf' has security, but secrets are required. 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  (ra0): device state change: 5 -> 6 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) complete. 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) started... 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  (ra0): device state change: 6 -> 4 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) complete. 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) starting... 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  (ra0): device state change: 4 -> 5 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  Activation (ra0/wireless): connection 'Auto 3conf' has security, and secrets exist.  No new secrets needed. 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  Config: added 'ssid' value '3conf' 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Dec 10 08:44:38 laroom-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec 10 08:44:38 laroom-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) complete. 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> disconnected 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  Config: set interface ap_scan to 1 
Dec 10 08:44:38 laroom-desktop NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
Dec 10 08:44:43 laroom-desktop kernel: [58763.641231] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
Dec 10 08:44:43 laroom-desktop kernel: [58763.682895] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
Dec 10 08:44:43 laroom-desktop kernel: [58763.741317] DRS: unkown mode,default use 11N 1S AP 
Dec 10 08:44:43 laroom-desktop kernel: [58763.741325] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
Dec 10 08:44:43 laroom-desktop NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
Dec 10 08:44:50 laroom-desktop kernel: [58770.806647] DRS: unkown mode,default use 11N 1S AP 
Dec 10 08:44:50 laroom-desktop kernel: [58770.806655] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
Dec 10 08:44:53 laroom-desktop NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected 
Dec 10 08:44:53 laroom-desktop NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
Dec 10 08:44:53 laroom-desktop NetworkManager: <info>  ra0: link timed out. 
Dec 10 08:45:08 laroom-desktop NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
Dec 10 08:45:08 laroom-desktop kernel: [58788.696112] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
Dec 10 08:45:08 laroom-desktop kernel: [58788.696615] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
Dec 10 08:45:08 laroom-desktop kernel: [58788.725116] DRS: unkown mode,default use 11N 1S AP 
Dec 10 08:45:08 laroom-desktop kernel: [58788.725124] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
Dec 10 08:45:15 laroom-desktop kernel: [58795.792288] DRS: unkown mode,default use 11N 1S AP 
Dec 10 08:45:15 laroom-desktop kernel: [58795.792296] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
Dec 10 08:45:18 laroom-desktop NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected 
Dec 10 08:45:18 laroom-desktop NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
Dec 10 08:45:33 laroom-desktop NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
Dec 10 08:45:33 laroom-desktop kernel: [58813.707151] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
Dec 10 08:45:33 laroom-desktop kernel: [58813.707450] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
Dec 10 08:45:33 laroom-desktop kernel: [58813.813225] DRS: unkown mode,default use 11N 1S AP 
Dec 10 08:45:33 laroom-desktop kernel: [58813.813233] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
Dec 10 08:45:33 laroom-desktop NetworkManager: <info>  ra0: link timed out. 
Dec 10 08:45:38 laroom-desktop NetworkManager: <info>  Activation (ra0/wireless): association took too long. 
Dec 10 08:45:38 laroom-desktop NetworkManager: <info>  (ra0): device state change: 5 -> 6 
Dec 10 08:45:38 laroom-desktop NetworkManager: <info>  Activation (ra0/wireless): asking for new secrets 
Dec 10 08:45:39 laroom-desktop NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected 
Dec 10 08:45:40 laroom-desktop kernel: [58820.888074] DRS: unkown mode,default use 11N 1S AP 
Dec 10 08:45:40 laroom-desktop kernel: [58820.888085] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
Dec 10 08:45:43 laroom-desktop NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1539 (get_secrets_dialog_response_cb): canceled. 
Dec 10 08:45:43 laroom-desktop NetworkManager: <info>  (ra0): device state change: 6 -> 9 
Dec 10 08:45:43 laroom-desktop NetworkManager: <info>  Activation (ra0) failed for access point (3conf) 
Dec 10 08:45:43 laroom-desktop NetworkManager: <info>  Marking connection 'Auto 3conf' invalid. 
Dec 10 08:45:43 laroom-desktop NetworkManager: <info>  Activation (ra0) failed. 
Dec 10 08:45:43 laroom-desktop NetworkManager: <info>  (ra0): device state change: 9 -> 3 
Dec 10 08:45:43 laroom-desktop NetworkManager: <info>  (ra0): deactivating device (reason: 0). 
Dec 10 08:45:43 laroom-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Dec 10 08:46:07 laroom-desktop kernel: [58847.079590] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
Dec 10 08:46:32 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
Dec 10 08:46:38 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
Dec 10 08:46:47 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
Dec 10 08:46:57 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
Dec 10 08:47:09 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
Dec 10 08:47:19 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
Dec 10 08:47:30 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
Dec 10 08:47:33 laroom-desktop dhclient: No DHCPOFFERS received.
Dec 10 08:47:33 laroom-desktop dhclient: No working leases in persistent database - sleeping.
Dec 10 08:48:07 laroom-desktop kernel: [58967.107432] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115

```sudo lshw -C network

```
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 02
       serial: 00:08:74:ac:92:39
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI duplex=full firmware=N/A ip=10.1.3.176 latency=64 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 00:25:9c:7c:bb:3c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT2870 Wireless
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 12:e8:f1:b6:cd:6e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```lsusb

```
Bus 001 Device 002: ID 1737:0077 Linksys 
```modinfo rt2870sta

```
filename:       /lib/modules/2.6.28-11-generic/updates/rt2870sta.ko
version:        1.4.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     E00168480A46C5501E5B1FD
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*
...
...
depends:        
vermagic:       2.6.28-11-generic SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)

```lsmod | grep rt2870sta
```
rt2870sta             502996  1 
```Any advice or help is greatly appreciated!

Thanks,

---

### Post by illuminaris on 2009-12-10
I did: sudo lshw -C network
Unfortunately, my wireless adapter doesn't even show up. It has eth0 and eth1 which are my standard ethernet interfaces that are always there no matter what. There is no mention of wireless anything or the ra0 alias.

*EDIT: modinfo for rt2870sta and rt3070sta both show a list of about 30 aliases. Is that normal?

---

### Post by eazylip on 2009-12-10
It looks like you've helped this guy out, so I have one for you.  I've purchased a Rosewill RNX-EasyN1 and a Azio AWU101N and both are not working with my 8.10.  I've used the available drivers installed through wine and I get a Enumerate Device error on the Rosewill install.  I get almost through the Azio installation, but when asked to input the device, it doesn't recognize it.  I can see the device and the green light is on.  Any ideas? Thanks - Wayne

---

### Post by b k on 2009-12-10
> **illuminaris said:**
>  When I go to edit the usb_main_dev.c file it doesn't have any text in it except my entry of the USB device code from the guide. Should there be anything else in that file? Or just what I was told to put in there?=)

Hi, there should be **plenty of stuff** in the file usb_main_dev.c. I have attached the content of what is in mine to give you an idea.

You should go back to Step 4  (post #182) **cd /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0** and make sure you are in the correct directory/path before executing **gedit os/linux/usb_main_dev.c **.
The folder **2009_1110_RT3070_Linux_STA_v2.1.2.0 **should **already be there** and somewhere in there is the file **os/linux/usb_main_dev.c **which you are trying to open for editing with the text editor **gedit** .

If this folder is not even there, go and read my **Before starting** instructions again carefully.

Here is what you should find in beginning part of your **os/linux/usb_main_dev.c **file (the line in bold below is what you are trying to add in):

/*
 *************************************************************************
 * Ralink Tech Inc.
 * 5F., No.36, Taiyuan St., Jhubei City,
 * Hsinchu County 302,
 * Taiwan, R.O.C.
 *
 * (c) Copyright 2002-2007, Ralink Technology, Inc.
 *
 * This program is free software; you can redistribute it and/or modify  * 
 * it under the terms of the GNU General Public License as published by  * 
 * the Free Software Foundation; either version 2 of the License, or     * 
 * (at your option) any later version.                                   * 
 *                                                                       * 
 * This program is distributed in the hope that it will be useful,       * 
 * but WITHOUT ANY WARRANTY; without even the implied warranty of        * 
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the         * 
 * GNU General Public License for more details.                          * 
 *                                                                       * 
 * You should have received a copy of the GNU General Public License     * 
 * along with this program; if not, write to the                         * 
 * Free Software Foundation, Inc.,                                       * 
 * 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.             * 
 *                                                                       * 
 *************************************************************************/

#include "rt_config.h"


// Following information will be show when you run 'modinfo'
// *** If you have a solution for the bug in current version of driver, please mail to me.
// Otherwise post to forum in ralinktech's web site([www.ralinktech.com]("http://www.ralinktech.com")) and let all users help you. ***
MODULE_AUTHOR("Paul Lin <paul_lin@ralinktech.com>");
MODULE_DESCRIPTION("RT2870 Wireless Lan Linux Driver");
MODULE_LICENSE("GPL");
#ifdef CONFIG_STA_SUPPORT
#ifdef MODULE_VERSION
MODULE_VERSION(STA_DRIVER_VERSION);
#endif
#endif // CONFIG_STA_SUPPORT //


/* module table */
struct usb_device_id rtusb_usb_id[] = {
#ifdef RT3070
    {USB_DEVICE(0x148F,0x3070)}, /* Ralink 3070 */
    {USB_DEVICE(0x148F,0x3071)}, /* Ralink 3071 */
    {USB_DEVICE(0x148F,0x3072)}, /* Ralink 3072 */
    {USB_DEVICE(0x0DB0,0x3820)}, /* Ralink 3070 */
    {USB_DEVICE(0x0DF6,0x003E)}, /* Sitecom 3070 */
    {USB_DEVICE(0x0DF6,0x0042)}, /* Sitecom 3072 */
    {USB_DEVICE(0x14B2,0x3C12)}, /* AL 3070 */
    {USB_DEVICE(0x18C5,0x0012)}, /* Corega 3070 */
    {USB_DEVICE(0x083A,0x7511)}, /* Arcadyan 3070 */
    {USB_DEVICE(0x1740,0x9703)}, /* EnGenius 3070 */
    {USB_DEVICE(0x1740,0x9705)}, /* EnGenius 3071 */
    {USB_DEVICE(0x1740,0x9706)}, /* EnGenius 3072 */
    {USB_DEVICE(0x13D3,0x3273)}, /* AzureWave 3070*/
    {USB_DEVICE(0x1044,0x800D)}, /* Gigabyte GN-WB32L 3070 */
    {USB_DEVICE(0x2019,0xAB25)}, /* Planex Communications, Inc. RT3070 */
    {USB_DEVICE(0x07B8,0x3070)}, /* AboCom 3070 */
    {USB_DEVICE(0x07B8,0x3071)}, /* AboCom 3071 */
    {USB_DEVICE(0x07B8,0x3072)}, /* Abocom 3072 */
    {USB_DEVICE(0x7392,0x7711)}, /* Edimax 3070 */
    {USB_DEVICE(0x1A32,0x0304)}, /* Quanta 3070 */
    {USB_DEVICE(0x1EDA,0x2310)}, /* AirTies 3070 */
    {USB_DEVICE(0x07D1,0x3C0A)}, /* D-Link 3072 */
    {USB_DEVICE(0x07D1,0x3C0D)}, /* D-Link 3070 */
    {USB_DEVICE(0x07D1,0x3C0E)}, /* D-Link 3070 */
    {USB_DEVICE(0x07D1,0x3C0F)}, /* D-Link 3070 */
    {USB_DEVICE(0x1D4D,0x000C)}, /* Pegatron Corporation 3070 */
    {USB_DEVICE(0x1D4D,0x000E)}, /* Pegatron Corporation 3070 */
    {USB_DEVICE(0x5A57,0x5257)}, /* Zinwell 3070 */
    {USB_DEVICE(0x5A57,0x0283)}, /* Zinwell 3072 */
    {USB_DEVICE(0x04BB,0x0945)}, /* I-O DATA 3072 */
    {USB_DEVICE(0x203D,0x1480)}, /* Encore 3070 */
    **{USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */**
#endif // RT3070 //
    { }/* Terminating entry */
};


Hope this helps you to progress further.

We have not given up on you yet - good luck!

---

### Post by dhom on 2009-12-10
Whenever I do 
cp -p /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2870sta.ko /lib/modules/`**uname** -r`/updatesI get an error saying that "no such file or directory" but when i do
**mkdir /lib/modules/`uname -r`/updates/` **it says that "file exists"; im also using 9.10, does that make a difference? please help :(

---

### Post by b k on 2009-12-10
Hello to all visitors to this thread. I am very new to Ubuntu.

I have been reading a lot especially on this thread.

My Wusb54gc v3 is currently working very well following procedure in #182 (which is a collection of steps taken from earlier posters + a little of my imput) and some tips in #187.

As there are so many different proposed solutions/workarounds (each with its **own specific set of ralink drivers**), it should be helpful if posters state which post #xxx that they are following when seeking assistance.

I believe that by now there is **more than one** workable solution/workaround within this thread. There is also **more than one** workable set of Ralink drivers.
Unfortunately, each time you update to a new kernel number, the wireless adapter stops working. 
Repeating the procedure with some minor modifications got the adapter up and running again.

Anyone trying for the first time should choose which ever set of procedure and recommended drivers and stick to it (at least for a while).
Mixing different drivers with any set of procedure is a bad idea in my opinion.

Always use copy and paste technique to get the commands into the Terminal. This minimises a lot of typing error.

Just my two cents worth!

---

### Post by b k on 2009-12-10
> **dhom said:**
> Whenever I do 
cp -p /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2870sta.ko /lib/modules/`**uname** -r`/updatesI get an error saying that "no such file or directory" but when i do
**mkdir /lib/modules/`uname -r`/updates/` **it says that "file exists"; im also using 9.10, does that make a difference? please help :(

Hi, I think you need to go to:

Applications Accessories Terminal

type **uname -r**

the output should be something like **2.6.31-xx-generic**

Copy and paste that in 'uname -r' into your commands but **without** the quotes '    '

Hope that helps

---

### Post by dhom on 2009-12-10
after i followed the guide in #182, the process worked! but after I restarted the machine after doing updates, the adapter wasn't recognized anymore, should I just redo all the steps or should I do something different, please help :(

---

### Post by b k on 2009-12-10
> **dhom said:**
> after i followed the guide in #182, the process worked! but after I restarted the machine after doing updates, the adapter wasn't recognized anymore, should I just redo all the steps or should I do something different, please help :(

Read the Special Notes in the post #182 but check what kernel number you have first:

the command in Terminal is [B]uname -r

[/B]The output is something like **2.6.31-1x-generic**

This is the kernel number I am talking about in the Special Notes.

Good luck and post if you succeed.

---

### Post by b k on 2009-12-10
Hello, I am trying to refine the steps in #182 and need some one to clarify this:

If I am running say 2.6.31-**14**-generic kernel and **double** click on say 2009_1110_RT3070_Linux_STA_v2[1].1.2.0.tar.bz2 file would the contents of the output files be **exactly** the same as if I was running say 2.6.31-**16**-generic kernel and did the same thing (ie double click).

Another similar question but for executing command **tar xjf 2009_1110_RT3070_Linux_STA_v2[1].1.2.0.tar.bz2**
Would the output files/content be exactly the same if executed under **differrent** generic kernel numbers.

Any help would be appreciated.

---

### Post by illuminaris on 2009-12-10
B K, whether I succeed or not, you are truly a saint. I hope there is some way I can repay you in this life or another.

Unfortunately, I was mistaken. I had already found the correct usb_main_dev.c file when I was following your guide. It was only the second time around that I had entered the wrong information. So the correct data was already in the usb_main_dev.c file and that won't be of any help.

Is there anything else I can do to check on why the adapter is not registering? Here are a few thoughts maybe you can work with...

1. Neither my ethernet ( which was originally working but isn't now ) nor my wireless USB adapter are working
2. I have not taken any steps except installing ndiswrapper ( which I have since installed ) and following the steps of guides #2 and #182. If there are any steps that should be taken post-guide perhaps you could inform me.
3. I don't appear to have any kind of network manager in my System -> Admin. All I have is "Network Tools".
4. When I updated to 9.10 it asked if I wanted to update Samba, I accepted.
5. Currently both the 2870 and 3070 drivers are installed based on the steps of guide #2 and #182, note that the steps of guide #2 never successfully completed. I got that "struct" no "fguid" error.
6. It appears that my USB device is detected by lsusb and yet not when I perform the lshw -C network command. I don't know the difference, but perhaps it's a clue.

That's about all I can think of, except that the light has never come on in my USB device. It hasn't worked even for a moment, while my ethernet cable worked up until yesterday.

Thank you again for your help!

*EDIT: I never noticed this before but when I run the gedit os/linux/usb_main_dev.c command I get this feedback repeated over and over again like 25 times.

> GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information (Details - 1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

*EDIT2: Someone in a Ubuntu chat sent me here -- [https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking) Though it's been absolutely no help to me, perhaps it could answer some of your questions.

---

### Post by b k on 2009-12-10
> **illuminaris said:**
> B K, whether I succeed or not, you are truly a saint. I hope there is some way I can repay you in this life or another.

Unfortunately, I was mistaken. I had already found the correct usb_main_dev.c file when I was following your guide. It was only the second time around that I had entered the wrong information. So the correct data was already in the usb_main_dev.c file and that won't be of any help.

Is there anything else I can do to check on why the adapter is not registering? Here are a few thoughts maybe you can work with...

1. Neither my ethernet ( which was originally working but isn't now ) nor my wireless USB adapter are working
2. I have not taken any steps except installing ndiswrapper ( which I have since installed ) and following the steps of guides #2 and #182. If there are any steps that should be taken post-guide perhaps you could inform me.
3. I don't appear to have any kind of network manager in my System -> Admin. All I have is "Network Tools".
4. When I updated to 9.10 it asked if I wanted to update Samba, I accepted.
5. Currently both the 2870 and 3070 drivers are installed based on the steps of guide #2 and #182, note that the steps of guide #2 never successfully completed. I got that "struct" no "fguid" error.
6. It appears that my USB device is detected by lsusb and yet not when I perform the lshw -C network command. I don't know the difference, but perhaps it's a clue.

That's about all I can think of, except that the light has never come on in my USB device. It hasn't worked even for a moment, while my ethernet cable worked up until yesterday.

Thank you again for your help!

*EDIT: I never noticed this before but when I run the gedit os/linux/usb_main_dev.c command I get this feedback repeated over and over again like 25 times.



*EDIT2: Someone in a Ubuntu chat sent me here -- [https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking) Though it's been absolutely no help to me, perhaps it could answer some of your questions.

LOL, Mother Teresa would be must disappointed that you have kind of made me into a saint for trying to help you salvage a dongle that probably cost 45 dollars!

The starting point for procedure in #182 was Ubuntu 9.10 OS desktop 32bits (kernel 2.6.31-14-generic) with the original NetworkManager installed using 2009_1110_RT3070_Linux_STA_v2[1].1.2.0.tar.bz2 Ralink driver.

Unfortunately your situation is more complicated because it appears that you have upgraded from an older Ubuntu OS and you have mixed different drivers with different procedures.

Could you:
1. Let me know which kernel number your OS is running on now.

2. If you would like to continue procedure in #182, please uninstall ndiswrapper and make sure that NetworkManager (which was the default network manager installed in Ubuntu 9.10) is currently installed. Check if you have a kind of wireless symbol with vertical bars of varying heights at the top of your screen - if you have, move your pointer over the symbol, right click and click about.

Do any removal and installation of the above from within Ubuntu Software Centre.
Do not be worried you can always go back in later to reinstall any software that you have removed earlier.


I just checked within my Ubuntu Software Centre and confirm that Samba is not installed on my system. I am unable to say if this is causing your problem.

If I am not mistaken your "fguid" error is some kind of a bug caused when you upgraded your I think bootloader GRUB to GRUB2.
I read about this somewhere on the internet but cannot be sure.

The procedure in #182 can be repeated without any problem (at least I did not have any). Probably some steps are redundant but for new folks like me (still trying to figure out whether some command output is dependent/independent of kernel numbers ) , redundancy is good.

Let see where you go from here - remember there is always plan Z.

Good luck

---

### Post by illuminaris on 2009-12-10
Ha ha, well, it's the thought that counts.

I am currently  using 2.6.31-16-generic
I can't download anything like networkmanager because my internet isn't working on Ubuntu machine. Is there a way to check if I have it? I believe I do, just not in System->Admin.

---

### Post by b k on 2009-12-11
> **illuminaris said:**
> Ha ha, well, it's the thought that counts.
 
I am currently using 2.6.31-16-generic
I can't download anything like networkmanager because my internet isn't working on Ubuntu machine. Is there a way to check if I have it? I believe I do, just not in System->Admin.
 
Go to :
 
Applications , Ubuntu Software Centre
 
Use the search feature and type in NetworkManager
 
Pick the correct one and click the arrow to its right.
 
Scroll down and you should have an install (or remove) option.
 
Could you also let me know your 2009_1110_RT3070_Linux_STA_v2[1].1.2.0.tar.bz2 directory/file path(ie, where you have this file on your system).

---

### Post by illuminaris on 2009-12-11
I followed your instructions.

1. I do apparently have NetworkManager, but it's not in System Preferences or Admin. I tried editing the menus to add it, but it's not there either. I also tried typing NetworkManager in terminal and it didn't give an error but it didn't load anything, just skipped to the next open line. Maybe I could put a tail on it but I don't know the command.

2. My tar file is in the directory you recommended in your guide at #182. home/illuminaris/Downloads

---

### Post by willrockformilk on 2009-12-11
I am at my whits end over here. Everytime i think i have it. I dont. :-/ 

It all has to do with authenticating and im suspecting im noting passing my WPAPSK correctly. Ca someone please help me?

tail -100 /var/log/syslog

```
Dec 11 10:14:54 laroom-desktop avahi-daemon[2451]: Registering new address record for fe80::225:9cff:fe7c:bb3c on ra0.*.
Dec 11 10:15:03 laroom-desktop kernel: [ 1537.528010] ra0: no IPv6 routers present
Dec 11 10:15:11 laroom-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Dec 11 10:15:11 laroom-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec 11 10:15:11 laroom-desktop dhclient: All rights reserved.
Dec 11 10:15:11 laroom-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Dec 11 10:15:11 laroom-desktop dhclient: 
Dec 11 10:15:12 laroom-desktop dhclient: Listening on LPF/ra0/00:25:9c:7c:bb:3c
Dec 11 10:15:12 laroom-desktop dhclient: Sending on   LPF/ra0/00:25:9c:7c:bb:3c
Dec 11 10:15:12 laroom-desktop dhclient: Sending on   Socket/fallback
Dec 11 10:15:13 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
Dec 11 10:15:17 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
Dec 11 10:15:22 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
Dec 11 10:15:31 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 19
Dec 11 10:15:50 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 17
Dec 11 10:16:07 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
Dec 11 10:16:14 laroom-desktop dhclient: No DHCPOFFERS received.
Dec 11 10:16:14 laroom-desktop dhclient: No working leases in persistent database - sleeping.
Dec 11 10:16:14 laroom-desktop avahi-autoipd(ra0)[5900]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Dec 11 10:16:14 laroom-desktop avahi-autoipd(ra0)[5900]: Successfully called chroot().
Dec 11 10:16:14 laroom-desktop avahi-autoipd(ra0)[5900]: Successfully dropped root privileges.
Dec 11 10:16:14 laroom-desktop avahi-autoipd(ra0)[5900]: Starting with address 169.254.6.234
Dec 11 10:16:19 laroom-desktop avahi-autoipd(ra0)[5900]: Callout BIND, address 169.254.6.234 on interface ra0
Dec 11 10:16:19 laroom-desktop avahi-daemon[2451]: Joining mDNS multicast group on interface ra0.IPv4 with address 169.254.6.234.
Dec 11 10:16:19 laroom-desktop avahi-daemon[2451]: New relevant interface ra0.IPv4 for mDNS.
Dec 11 10:16:19 laroom-desktop avahi-daemon[2451]: Registering new address record for 169.254.6.234 on ra0.IPv4.
Dec 11 10:16:23 laroom-desktop avahi-autoipd(ra0)[5900]: Successfully claimed IP address 169.254.6.234
Dec 11 10:16:48 laroom-desktop kernel: [ 1642.642546] Terminate the TimerQThr_pid=5780!
Dec 11 10:16:48 laroom-desktop kernel: [ 1642.642597] Terminate the MLMEThr_pid=5778!
Dec 11 10:16:48 laroom-desktop kernel: [ 1642.642614] Terminate the RTUSBCmdThr_pid=5779!
Dec 11 10:16:48 laroom-desktop avahi-daemon[2451]: Interface ra0.IPv4 no longer relevant for mDNS.
Dec 11 10:16:48 laroom-desktop avahi-daemon[2451]: Leaving mDNS multicast group on interface ra0.IPv4 with address 169.254.6.234.
Dec 11 10:16:48 laroom-desktop avahi-autoipd(ra0)[5900]: SIOCSIFFLAGS failed: Permission denied
Dec 11 10:16:48 laroom-desktop avahi-autoipd(ra0)[5900]: Callout STOP, address 169.254.6.234 on interface ra0
Dec 11 10:16:48 laroom-desktop dhclient: receive_packet failed on ra0: Network is down
Dec 11 10:16:48 laroom-desktop kernel: [ 1642.649576] ---> RTMPFreeTxRxRingMemory
Dec 11 10:16:48 laroom-desktop kernel: [ 1642.649624] <--- ReleaseAdapter
Dec 11 10:16:48 laroom-desktop avahi-daemon[2451]: Withdrawing address record for fe80::225:9cff:fe7c:bb3c on ra0.
Dec 11 10:16:48 laroom-desktop avahi-daemon[2451]: Withdrawing address record for 169.254.6.234 on ra0.
Dec 11 10:16:48 laroom-desktop avahi-autoipd(ra0)[5901]: client: RTNETLINK answers: No such process
Dec 11 10:16:56 laroom-desktop dhclient: There is already a pid file /var/run/dhclient.pid with pid 5917
Dec 11 10:16:56 laroom-desktop dhclient: killed old client process, removed PID file
Dec 11 10:16:56 laroom-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Dec 11 10:16:56 laroom-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec 11 10:16:56 laroom-desktop dhclient: All rights reserved.
Dec 11 10:16:56 laroom-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Dec 11 10:16:56 laroom-desktop dhclient: 
Dec 11 10:16:56 laroom-desktop dhclient: Listening on LPF/ra0/00:25:9c:7c:bb:3c
Dec 11 10:16:56 laroom-desktop dhclient: Sending on   LPF/ra0/00:25:9c:7c:bb:3c
Dec 11 10:16:56 laroom-desktop dhclient: Sending on   Socket/fallback
Dec 11 10:17:02 laroom-desktop /USR/SBIN/CRON[5978]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.114076] <-- RTMPAllocTxRxRingMemory, Status=0
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.117070] -->RTUSBVenderReset
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.117191] <--RTUSBVenderReset
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.395631] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.395673] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.395714] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.395757] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.406851] 1. Phy Mode = 5
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.406856] 2. Phy Mode = 5
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.437770] RTMPSetPhyMode: channel is out of range, use first channel=1 
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.451138] 3. Phy Mode = 9
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.459139] MCS Set = ff 00 00 00 01
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.531880] <==== RTMPInitialize, Status=0
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.533498] 0x1300 = 00064300
Dec 11 10:17:17 laroom-desktop avahi-daemon[2451]: Registering new address record for fe80::225:9cff:fe7c:bb3c on ra0.*.
Dec 11 10:17:26 laroom-desktop kernel: [ 1679.888011] ra0: no IPv6 routers present
Dec 11 10:18:56 laroom-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Dec 11 10:18:56 laroom-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec 11 10:18:56 laroom-desktop dhclient: All rights reserved.
Dec 11 10:18:56 laroom-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Dec 11 10:18:56 laroom-desktop dhclient: 
Dec 11 10:18:57 laroom-desktop dhclient: Listening on LPF/ra0/00:25:9c:7c:bb:3c
Dec 11 10:18:57 laroom-desktop dhclient: Sending on   LPF/ra0/00:25:9c:7c:bb:3c
Dec 11 10:18:57 laroom-desktop dhclient: Sending on   Socket/fallback
Dec 11 10:18:58 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
Dec 11 10:19:04 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
Dec 11 10:19:15 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13
Dec 11 10:19:28 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 17
Dec 11 10:19:45 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
Dec 11 10:19:59 laroom-desktop dhclient: No DHCPOFFERS received.
Dec 11 10:19:59 laroom-desktop dhclient: No working leases in persistent database - sleeping.
Dec 11 10:19:59 laroom-desktop avahi-autoipd(ra0)[6290]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Dec 11 10:19:59 laroom-desktop avahi-autoipd(ra0)[6290]: Successfully called chroot().
Dec 11 10:19:59 laroom-desktop avahi-autoipd(ra0)[6290]: Successfully dropped root privileges.
Dec 11 10:19:59 laroom-desktop avahi-autoipd(ra0)[6290]: Starting with address 169.254.6.234
Dec 11 10:20:01 laroom-desktop /USR/SBIN/CRON[6302]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 11 10:20:04 laroom-desktop avahi-autoipd(ra0)[6290]: Callout BIND, address 169.254.6.234 on interface ra0
Dec 11 10:20:04 laroom-desktop avahi-daemon[2451]: Joining mDNS multicast group on interface ra0.IPv4 with address 169.254.6.234.
Dec 11 10:20:04 laroom-desktop avahi-daemon[2451]: New relevant interface ra0.IPv4 for mDNS.
Dec 11 10:20:04 laroom-desktop avahi-daemon[2451]: Registering new address record for 169.254.6.234 on ra0.IPv4.
Dec 11 10:20:08 laroom-desktop avahi-autoipd(ra0)[6290]: Successfully claimed IP address 169.254.6.234
Dec 11 10:26:08 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
Dec 11 10:26:11 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
Dec 11 10:26:19 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 21
Dec 11 10:26:40 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
Dec 11 10:26:48 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
Dec 11 10:26:56 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
Dec 11 10:27:09 laroom-desktop dhclient: No DHCPOFFERS received.
Dec 11 10:27:09 laroom-desktop dhclient: No working leases in persistent database - sleeping.
```dmesg | grep ra0

```
[   27.885285] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[   27.885326] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[   27.885367] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[   27.885409] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[   38.116030] ra0: no IPv6 routers present
[   77.423141] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[   77.423184] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[   77.423225] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[   77.423267] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[   88.500049] ra0: no IPv6 routers present
[  317.150146] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[  317.150189] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[  317.150230] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[  317.150272] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[  327.768023] ra0: no IPv6 routers present
[  394.851313] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[  394.851357] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[  394.851398] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[  394.851440] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[  405.816025] ra0: no IPv6 routers present
[  670.312094] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[  670.312136] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[  670.312177] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[  670.312219] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[  675.059914] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[  675.059957] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[  675.059998] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[  675.060061] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[  685.732016] ra0: no IPv6 routers present
[  873.875269] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[  873.875312] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[  873.875353] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[  873.875395] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[  884.644014] ra0: no IPv6 routers present
[ 1526.559231] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[ 1526.559273] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[ 1526.559315] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[ 1526.559357] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[ 1537.528010] ra0: no IPv6 routers present
[ 1669.395631] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[ 1669.395673] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[ 1669.395714] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[ 1669.395757] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[ 1679.888011] ra0: no IPv6 routers present
```I think the obvious problem is that our ra0 is not authenticating (obviously) and it has to do with:

```
I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
```I have tried wpa_supplicant to connect. And have even tried:

```
sudo ifconfig [interface] down
sudo dhclient -r [interface]
sudo ifconfig [interface] up
sudo iwconfig [inteface] essid &#8220;ESSID_IN_QUOTES&#8221;
sudo iwpriv [interface] set AuthMode=WPAPSK
sudo iwpriv [interface] set EncrypType=TKIP
sudo iwpriv [interface] set WPAPSK=&#8221;YOUR_WPA_PSK_KEY&#8221;
sudo dhclient [interface]
```Which was found here: [http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html/comment-page-1](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html/comment-page-1)

I believe there is something about the tutorial on [http://newyork.ubuntuforums.org/showthread.php?t=1155941](http://newyork.ubuntuforums.org/showthread.php?t=1155941) that overides normal authentication procedures and uses the /etc/Wireless/RT2870STA/RT2870STA.dat file for the source of authentication. However all my information in that file is correct and im somewhat at a loss as to what to do.

Which in that file i have tried both using the raw password and using the encrypted pass via:

```
wpa_passphrase your_essid your_passphrase
```RT2870STA.dat:

```
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=11n-AP
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=WPA2
EncrypType=TKIP
WPAPSK=036223a995db109fd2420d54f19f885fc87eb8c596d03299e60b0bc354bb6af3
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
FastRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=1
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0
```

Anyone else have any ideas?

---

### Post by willrockformilk on 2009-12-11
I am using WICD but mostly i am trying to connect from the command line using dhclient. But none of any of the combinations of this thread have worked for me. 

What am i missing exactly?

Here is some info: 

uname -r
```
2.6.28-11-generic
```

lsusb:
```
Bus 001 Device 002: ID 1737:0077 Linksys
```

lsmod | grep re2870sta:
```
rt2870sta             508372  1
```

modinfo rt2870sta:
```
filename:       /lib/modules/2.6.28-11-generic/updates/rt2870sta.ko
version:        1.4.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     E00168480A46C5501E5B1FD
[COLOR=Red]alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*[/COLOR]
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.28-11-generic SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)

```


dmesg while connecting
```
[  216.759773] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[  222.008415] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  223.416410] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[  223.416582] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  234.392022] eth0: no IPv6 routers present
[ 1774.377807] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[ 1776.270716] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[ 1786.699368] Terminate the TimerQThr_pid=2354!
[ 1786.699418] Terminate the MLMEThr_pid=2352!
[ 1786.699435] Terminate the RTUSBCmdThr_pid=2353!
[ 1786.706320] ---> RTMPFreeTxRxRingMemory
[ 1786.706598] <--- ReleaseAdapter
[ 1787.552863] <-- RTMPAllocTxRxRingMemory, Status=0
[ 1787.554950] -->RTUSBVenderReset
[ 1787.555074] <--RTUSBVenderReset
[ 1787.908432] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[ 1787.908474] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[ 1787.908515] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[ 1787.908556] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[ 1787.909732] 1. Phy Mode = 9
[ 1787.909735] 2. Phy Mode = 9
[ 1787.939269] RTMPSetPhyMode: channel is out of range, use first channel=1 
[ 1787.952510] 3. Phy Mode = 9
[ 1787.960012] MCS Set = ff 00 00 00 01
[ 1788.033255] <==== RTMPInitialize, Status=0
[ 1788.034746] 0x1300 = 00064300
[ 1788.461690] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[ 1798.804024] ra0: no IPv6 routers present
[ 1803.438789] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[ 1803.438955] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[ 1818.440606] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[ 1818.440782] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[ 1830.131688] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[ 1833.562123] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115
[ 1838.763580] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 115

```

tail -50 /var/log/syslog:
```
Dec 11 12:38:53 laroom-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Dec 11 12:38:53 laroom-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec 11 12:38:53 laroom-desktop dhclient: All rights reserved.
Dec 11 12:38:53 laroom-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Dec 11 12:38:53 laroom-desktop dhclient: 
Dec 11 12:38:53 laroom-desktop dhclient: Bind socket to interface: No such device
Dec 11 12:38:53 laroom-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Dec 11 12:38:53 laroom-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec 11 12:38:53 laroom-desktop dhclient: All rights reserved.
Dec 11 12:38:53 laroom-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Dec 11 12:38:53 laroom-desktop dhclient: 
Dec 11 12:38:53 laroom-desktop dhclient: Bind socket to interface: No such device
Dec 11 12:38:53 laroom-desktop kernel: [ 1850.170033] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 11 12:38:53 laroom-desktop kernel: [ 1850.486545] Terminate the TimerQThr_pid=5934!
Dec 11 12:38:53 laroom-desktop kernel: [ 1850.486629] Terminate the MLMEThr_pid=5932!
Dec 11 12:38:53 laroom-desktop kernel: [ 1850.486649] Terminate the RTUSBCmdThr_pid=5933!
Dec 11 12:38:53 laroom-desktop avahi-daemon[2454]: Withdrawing address record for fe80::225:9cff:fe7c:bb3c on ra0.
Dec 11 12:38:53 laroom-desktop kernel: [ 1850.506546] ---> RTMPFreeTxRxRingMemory
Dec 11 12:38:53 laroom-desktop kernel: [ 1850.507405] <--- ReleaseAdapter
Dec 11 12:38:53 laroom-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Dec 11 12:38:53 laroom-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec 11 12:38:53 laroom-desktop dhclient: All rights reserved.
Dec 11 12:38:53 laroom-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Dec 11 12:38:53 laroom-desktop dhclient: 
Dec 11 12:38:54 laroom-desktop dhclient: Listening on LPF/eth0/00:08:74:ac:92:39
Dec 11 12:38:54 laroom-desktop dhclient: Sending on   LPF/eth0/00:08:74:ac:92:39
Dec 11 12:38:54 laroom-desktop dhclient: Sending on   Socket/fallback
Dec 11 12:38:54 laroom-desktop dhclient: DHCPREQUEST of 10.1.3.176 on eth0 to 255.255.255.255 port 67
Dec 11 12:38:54 laroom-desktop kernel: [ 1851.760382] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
Dec 11 12:38:54 laroom-desktop kernel: [ 1851.760526] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 11 12:38:56 laroom-desktop avahi-daemon[2454]: Registering new address record for fe80::208:74ff:feac:9239 on eth0.*.
Dec 11 12:39:02 laroom-desktop dhclient: DHCPREQUEST of 10.1.3.176 on eth0 to 255.255.255.255 port 67
Dec 11 12:39:05 laroom-desktop kernel: [ 1862.056023] eth0: no IPv6 routers present
Dec 11 12:39:15 laroom-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Dec 11 12:39:22 laroom-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Dec 11 12:39:32 laroom-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Dec 11 12:39:45 laroom-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Dec 11 12:39:45 laroom-desktop dhclient: DHCPOFFER of 10.1.3.176 from 10.1.1.2
Dec 11 12:39:45 laroom-desktop dhclient: DHCPREQUEST of 10.1.3.176 on eth0 to 255.255.255.255 port 67
Dec 11 12:39:45 laroom-desktop dhclient: DHCPACK of 10.1.3.176 from 10.1.1.2
Dec 11 12:39:45 laroom-desktop avahi-daemon[2454]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.1.3.176.
Dec 11 12:39:45 laroom-desktop avahi-daemon[2454]: New relevant interface eth0.IPv4 for mDNS.
Dec 11 12:39:45 laroom-desktop avahi-daemon[2454]: Registering new address record for 10.1.3.176 on eth0.IPv4.
Dec 11 12:39:45 laroom-desktop avahi-daemon[2454]: Withdrawing address record for 10.1.3.176 on eth0.
Dec 11 12:39:45 laroom-desktop avahi-daemon[2454]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.1.3.176.
Dec 11 12:39:45 laroom-desktop avahi-daemon[2454]: Interface eth0.IPv4 no longer relevant for mDNS.
Dec 11 12:39:45 laroom-desktop avahi-daemon[2454]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.1.3.176.
Dec 11 12:39:45 laroom-desktop avahi-daemon[2454]: New relevant interface eth0.IPv4 for mDNS.
Dec 11 12:39:45 laroom-desktop avahi-daemon[2454]: Registering new address record for 10.1.3.176 on eth0.IPv4.
Dec 11 12:39:45 laroom-desktop dhclient: bound to 10.1.3.176 -- renewal in 119148 seconds.

```

iwlist ra0 scan:
```
ra0       Scan completed :
          Cell 01 - Address: 00:13:10:FD:C3:92
                    ESSID:"3conf"
                    Mode:Managed
                    Channel:6
                    Quality:15/100  Signal level:-84 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```

lshw -class network
```
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 02
       serial: 00:08:74:ac:92:39
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI firmware=N/A ip=10.1.3.176 latency=64 mingnt=255 module=e1000 multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 00:25:9c:7c:bb:3c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT2870 Wireless
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5e:b9:66:db:2d:c0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

/bin/ls -ltr /etc/Wireless/*

I initially install the rt2870sta it didnt work so i uninstalled it and tried the tutorial on #182 with the rt3070sta drivers hence why there is a 3070 folder currently.

```
/etc/Wireless/RT2870STA:
total 8
-rw-r--r-- 1 root root  742 2009-12-11 11:34 RT2870STA.dat~
-rw-r--r-- 1 root root 1025 2009-12-11 12:07 RT2870STA.dat

/etc/Wireless/RT3070STA:
total 4
-rwxr-xr-x 1 root root 1025 2009-12-11 12:01 RT2870STA.dat
```

/bin/ls -ltr /lib/modules/`uname -r`/updates/

```
total 1220
-rw-r--r-- 1 root root 612814 2009-12-11 11:31 rt2870sta.ko
-rw-r--r-- 1 root root 623332 2009-12-11 12:01 rt3070sta.ko
```

---

### Post by illuminaris on 2009-12-11
Dear Mr. B K,

I would just like to inform you that I did a complete reinstall of Ubuntu 9.10 ( Plan Z! ) and followed your guide #182 from beginning to end. Now my wireless adapter works PERFECTLY! Thank you so much for all your help, I don't care what Mother Theresa says, you ARE a saint. :)

Good luck to everyone else, I really hope you get to experience the excitement of success. Thank you to everyone else who helped as well, and who contributed to this thread.

---

### Post by DSR01 on 2009-12-11
I need serious help I have tried both ways on the post to install this driver. Both have not worked at all. COn Step 6 I get errors after make and install...

---

### Post by flhtguy on 2009-12-12
What errors are you receiving?

---

### Post by mephare on 2009-12-12
Hey guys... completely new at Linux and having some issues setting this up... i believe its step 7, i get this error:

cp: cannot stat '/kernel/drivers/net/wireless/rt2870sta.ko' No such file or directory. Please help, I'm stuck browsing the web via PS3 and Phone =)

---

### Post by georgeg on 2009-12-15
BK....

In step 5, you have this:
[B]Code:
gedit os/linux/usb_main_dev.c and add the following line

Code:
{USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */
[/B]

Where do you get this information?  My wireless adapter is a different one (Azio AWU101N, Ralink chipset).  I've looked thru the Win7 hardware info and can't find anything similar.  I'm trying to run your instruction set on my Mint 8-64 install which has a slightly different file structure but it is ubuntu based and uses the 2.6.31-14-generic kernal.

---

### Post by b k on 2009-12-16
> **georgeg said:**
> BK....

In step 5, you have this:
[B]Code:
gedit os/linux/usb_main_dev.c and add the following line

Code:
{USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */
[/B]

Where do you get this information?  My wireless adapter is a different one (Azio AWU101N, Ralink chipset).  I've looked thru the Win7 hardware info and can't find anything similar.  I'm trying to run your instruction set on my Mint 8-64 install which has a slightly different file structure but it is ubuntu based and uses the 2.6.31-14-generic kernal.

Hi, I am quite new to Ubuntu and have not use Mint 8-64 but see if the info below helps.

I have refined the procedures in #182 of this thread and posted it at another thread at this link [http://ubuntuforums.org/showthread.php?t=1353044](http://ubuntuforums.org/showthread.php?t=1353044) post #1

Which ever thread/post that you are following ensure that you use those attached files at the end ot the relevant thread/post.

Open a Terminal window and type:

*lsusb*

You should get something like (depends on the usb  wireless adapter you have)

Bus 005 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/2/4GB Flash Drive
Bus 002 Device 003: ID **1737:0077** Linksys 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Below is an extract of usb devices supported by Ralink 2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2 driver.

After extraction, the info below can be found in a file usb_main_dev.c located at os/linux/usb_main_dev.c within the file 2009_1110_RT3070_Linux_STA_v2.1.2.0 by executing steps 4 and 5.

The info below is extracted from one of the files within the above ralink driver.

#ifdef RT3070
    {USB_DEVICE(0x148F,0x3070)}, /* Ralink 3070 */
    {USB_DEVICE(0x148F,0x3071)}, /* Ralink 3071 */
    {USB_DEVICE(0x148F,0x3072)}, /* Ralink 3072 */
    {USB_DEVICE(0x0DB0,0x3820)}, /* Ralink 3070 */
    {USB_DEVICE(0x0DF6,0x003E)}, /* Sitecom 3070 */
    {USB_DEVICE(0x0DF6,0x0042)}, /* Sitecom 3072 */
    {USB_DEVICE(0x14B2,0x3C12)}, /* AL 3070 */
    {USB_DEVICE(0x18C5,0x0012)}, /* Corega 3070 */
    {USB_DEVICE(0x083A,0x7511)}, /* Arcadyan 3070 */
    {USB_DEVICE(0x1740,0x9703)}, /* EnGenius 3070 */
    {USB_DEVICE(0x1740,0x9705)}, /* EnGenius 3071 */
    {USB_DEVICE(0x1740,0x9706)}, /* EnGenius 3072 */
    {USB_DEVICE(0x13D3,0x3273)}, /* AzureWave 3070*/
    {USB_DEVICE(0x1044,0x800D)}, /* Gigabyte GN-WB32L 3070 */
    {USB_DEVICE(0x2019,0xAB25)}, /* Planex Communications, Inc. RT3070 */
    {USB_DEVICE(0x07B8,0x3070)}, /* AboCom 3070 */
    {USB_DEVICE(0x07B8,0x3071)}, /* AboCom 3071 */
    {USB_DEVICE(0x07B8,0x3072)}, /* Abocom 3072 */
    {USB_DEVICE(0x7392,0x7711)}, /* Edimax 3070 */
    {USB_DEVICE(0x1A32,0x0304)}, /* Quanta 3070 */
    {USB_DEVICE(0x1EDA,0x2310)}, /* AirTies 3070 */
    {USB_DEVICE(0x07D1,0x3C0A)}, /* D-Link 3072 */
    {USB_DEVICE(0x07D1,0x3C0D)}, /* D-Link 3070 */
    {USB_DEVICE(0x07D1,0x3C0E)}, /* D-Link 3070 */
    {USB_DEVICE(0x07D1,0x3C0F)}, /* D-Link 3070 */
    {USB_DEVICE(0x1D4D,0x000C)}, /* Pegatron Corporation 3070 */
    {USB_DEVICE(0x1D4D,0x000E)}, /* Pegatron Corporation 3070 */
    {USB_DEVICE(0x5A57,0x5257)}, /* Zinwell 3070 */
    {USB_DEVICE(0x5A57,0x0283)}, /* Zinwell 3072 */
    {USB_DEVICE(0x04BB,0x0945)}, /* I-O DATA 3072 */
    {USB_DEVICE(0x203D,0x1480)}, /* Encore 3070 */

Once you have your usb device ID, find out which Ralink driver you need to us.

As your adapter description does not seem to be on the RT3070 list above, you may need to use another driver RT3090. I am not sure.

But again Linksys Wusb54gc v3 is also not in the above list but we have kind of maually added it in and got it to work with a lot of input from the people in this forum!

If you continue with procedure in #182 of this thread don't forget to **save and close **after you input/change any info in the files during the various steps.

Ensure that you configure your gateway/router **to broadcast your SSID** (network name) as I discovered that the wireless connection works erratically for 'hidden' networks.


Good luck

---

### Post by georgeg on 2009-12-17
Thanks BK.  I used your new script and it worked like a champ.  I'm online now with the 64bit version of Mint 8.

---

### Post by b k on 2009-12-17
> **georgeg said:**
> Thanks BK. I used your new script and it worked like a champ. I'm online now with the 64bit version of Mint 8.
 
Congratulations!
 
Remember once you upgrade your kernel, your connection will be broken again.
 
Just curious, is your gateway/router configured to broadcast or is it 'hidden'.

---

### Post by georgeg on 2009-12-17
> **b k said:**
> 
 
Just curious, is your gateway/router configured to broadcast or is it 'hidden'.

Hidden.  So far, its working very nicely.  We'll see what happens when I go into Mint tonight.  I saw your comments about not running "hidden".  It hasn't been a problem before but then this is a new wireless adapter and we'll just have to see.  I've been using it for about 3 wks now in Win7 and so far, I like it a heck of a lot better than my previous Linksys adapter.

You say you're not an expert in Ubuntu....Maybe not but you set up the best wireless solution I've found in three years of fighting wireless connections in Linux.  The idea of preparing a text file so that commands could be copied & pasted is something I wish I had thought of.  There have been other scripts I've run to get things going but I always had to print them out and key them in, stroke by stroke.  Your way is MUCH better and less susceptable to error.  Thanks again for thinking of it.

---

### Post by Addict2ToTux on 2009-12-28
I am one of unlucky guys here. I went through all posts and only found out the root cause of not working on my box. 

A short summary - If you are using a fresh-installed jaunty ("Ubuntu 9.04"), the driver built from 009_0525_RT3070_Linux_STA_v2.1.1.0.bz2 would finally set up the connection. 

However, I don't want to re-install the OS. The strange thing is I set up the connection ONCE with 2008_0925_RT2870_Linux_STA_v1.4.0.0.bz2; but can't repeat the process. I remembered after the step "apt-get install build-essential", I just can't set up the connection any more. Later I tried with RT3070 package but still without any luck. 

I noticed both RT2870 and RT3070 drivers generate some errors in /var/log/message:

> 
Dec 28 13:45:35 ness kernel: [ 1558.173638] 1. Phy Mode = 9
Dec 28 13:45:35 ness kernel: [ 1558.173641] 2. Phy Mode = 9
Dec 28 13:45:35 ness kernel: [ 1558.217491] 3. Phy Mode = 9
Dec 28 13:45:35 ness kernel: [ 1558.225618] MCS Set = ff 00 00 00 01
Dec 28 13:45:35 ness kernel: [ 1558.272130] <==== rt28xx_init, Status=0
Dec 28 13:45:35 ness kernel: [ 1558.273622] 0x1300 = 00064300
Dec 28 13:45:37 ness kernel: [ 1559.782410] 0:3 LTL=0 , TL=0 L:0
Dec 28 13:45:37 ness kernel: [ 1559.782525] Bulk Out MLME Failed, Status=-2!
Dec 28 13:45:39 ness kernel: [ 1561.790279] 0:3 LTL=0 , TL=0 L:0
Dec 28 13:45:39 ness kernel: [ 1561.790395] Bulk Out MLME Failed, Status=-2!
Dec 28 13:45:40 ness kernel: [ 1563.405269] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 404
Dec 28 13:45:41 ness kernel: [ 1563.798272] 0:3 LTL=0 , TL=0 L:0
Dec 28 13:45:41 ness kernel: [ 1563.798390] Bulk Out MLME Failed, Status=-2!
Dec 28 13:45:43 ness kernel: [ 1565.806267] 0:3 LTL=0 , TL=0 L:0
Dec 28 13:45:43 ness kernel: [ 1565.806382] Bulk Out MLME Failed, Status=-2!
Dec 28 13:45:45 ness kernel: [ 1567.810260] 0:3 LTL=0 , TL=0 L:0
Dec 28 13:45:45 ness kernel: [ 1567.810376] Bulk Out MLME Failed, Status=-2!
Dec 28 13:45:46 ness kernel: [ 1568.719171] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=1!
Dec 28 13:45:46 ness kernel: [ 1568.867071] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=2!
Dec 28 13:45:46 ness kernel: [ 1569.015230] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=3!
Dec 28 13:45:46 ness kernel: [ 1569.163005] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=4!
Dec 28 13:45:46 ness kernel: [ 1569.311023] Qidx(0), not enough space in MgmtRin


I guess that is the problem. The lamp on my WUSB54GC dangle was never on.

---

### Post by KherKhere on 2010-01-04
Hello , 
i Have WUSB54GC V3 and BackTrack4 Pre Final 
i installed my Wlan Driver and my Wireless Card work well i can see other Access point with the iwlist ra0 scan Command , but when i type Airodump-ng ra0 it not show to me any Access point and again i type iwlist ra0 scan i saw error message Interface Dosent support scanning for solve this issue i must down and up again interface but same problem for airodump-ng

---

### Post by utrrrongeeb on 2010-01-07
I used the instructions in [post #2](http://ubuntuforums.org/showpost.php?p=7262158&postcount=2) to get a WUSB54GCv3 working in Debian Etch. Thanks radixor! :)

It initially wouldn't turn on, failing with some DMA/memory-related errors. Following instructions on [post #23](http://ubuntuforums.org/showpost.php?p=7291698&postcount=23), it appears DHCP was partially to blame, and it worked.

I added it to /etc/network/interfaces, with DHCP, it works fine, with WPA2 on a hidden WLAN, without (AFAIK) wpa_supplicant.

---

### Post by Theoutdoorsman on 2010-01-18
Can anyone confirm this will work with Ubuntu 9.10? 

Please see my recent thread here:
[http://ubuntuforums.org/showthread.php?p=8682954#post8682954](http://ubuntuforums.org/showthread.php?p=8682954#post8682954)

---

### Post by jimbob on 2010-01-18
Follow post #182 on page 19 of this thread and it will work in 9.10 Ubuntu.

---

### Post by deuz on 2010-01-18
Tx to b k for the guide & jimbob for pointing to it=) works like charm on 9.10 - 2.6.31-16-generic =)

---

### Post by Ancientfall on 2010-02-05
I believe I had the drivers installed correctly in my 9.10 ubuntu install. The problem I am having is when the device is in monitor mode and I try to see any APs I get nothing. I am sitting 1 foot away from my own AP and i get nothing on airodump when its in managed mode. Any suggestions?

---

### Post by BillJohnson on 2010-02-20
A very big thanks to "B K" and his post #182. I understand that you mostly just gathered together the information, but you put it in one spot, made a coherent procedure to follow and thanks to your effort, I now have the WUSB54GC Ver.3 up and running on 9.10 (32-bit). 

I am still dealing with that it won't work when the SSID is not broadcast (never accepts the passwords), but at least it is working with WPAPSK/TKIP with SSID broadcast enabled.

Thanks again - I was starting to lose all hope and was probably going to return/exchange for a PCI card - which I didn't really want to do because PCI is dead and when this machine is retired, I can reuse the USB somewhere else.

::guitar:

---

### Post by b k on 2010-02-20
> **BillJohnson said:**
>  
 
[COLOR=black]I am still dealing with that it won't work when the SSID is not broadcast (never accepts the passwords), but at least it is working with WPAPSK/TKIP with SSID broadcast enabled.[/COLOR]

::guitar:
 
 
 
Hi, thanks for the compliment.
 
The reason that you are having problem with 'hidden' networks is due to a bug in the NetworkManager.
 
I have 'refined' the procedure in post #182 and posted it at this link [http://ubuntuforums.org/showthread.php?t=1353044](http://ubuntuforums.org/showthread.php?t=1353044) .
 
Remember that your wireless adapter will fail to work again *once you update to a newer kernel number*. You need to see the new thread above and pick the correct procedure to follow once that happens to get your adapter up and running again.
 
At some point in time you may like to also try a more 'permanent' solution at this link [COLOR=#008000][https://launchpad.net/bugs/446889](https://launchpad.net/bugs/446889) [/COLOR][COLOR=black](see post #68 and #69 there).[/COLOR]
[COLOR=black]I have however not personally tried this particular solution yet.[/COLOR]

[COLOR=black]Your comments and feedback is most valuable.[/COLOR]

---

### Post by BillJohnson on 2010-02-27
I know about NetworkManager... I have tangled with it before. It's not very well written and sometimes I think it causes more problems than it solves.... That's how I knew to try and turn on broadcasting the SSID once the led on the wireless looked alive...

I understand re: new kernels. I put together this machine specifically for my mother, she's a newbie at computers. I disabled all updates so no new kernels. I had done a complete update before I started, so it will be up-to-date for a while. When I visit her I will check to see if there are any updates and be prepared to recompile, if a new kernel is available. I kept the source and instructions on another partition on that machine, just for reference. 

I, myself, generally stick to LTS releases. I only went to 9.10 because I had hoped that the support would already have been in the kernel, but it wasn't. Maybe with 10.04, which I think will be an LTS. I am looking forward to it.

Recompiling software for new kernels has to be one of linux's greatest weaknesses. Until HLL (His Lord Linus) decides to freeze kernel API's and keep compatibility for predetermined releases, I don't believe linux will ever go mainstream.. This also scares 3rd party OEM software providers, so they never offer their products for linux - support would be a nightmare for them. But linux is still fun to play with, just not for the general public that "just want things to work" (IJW - It Just Works)...

---

### Post by savook on 2010-03-10
Radixor, 

Recently, I purchased WUSB54GCv3 Wireless adapter and it didn't work on my xubuntu 9.04 kernel version 2.6.28-14-generic. 
I followed the steps that you have suggested in the tread posted on May 12th, 2009. I could see wireless network but couldn't able to connect to it. What may be wrong?
Could you please help me to resolve this issue.

Thanks in advance!

Savook

---

### Post by utrrrongeeb on 2010-03-10
> **savook said:**
> I could see wireless network but couldn't able to connect to it.

Is the WiFi network 'hidden' (not broadcasting its SSID)?

Are you seeing the network from the NetworkManager menu, or from a command like iwconfig?

Does the WiFi network have encryption?

---

### Post by sandy8925 on 2010-03-12
hey I don't know if anyone else knows this but just adding :
blacklist rt2800usb
to /etc/modprobe.d/blacklist.conf and rebooting makes it work!

I was really surprised to discover this. I did it on a fresh karmic install and it worked. I used lsmod | grep rt to discover that it was using rt2870sta drivers.And the light works too!

NOTE - I compiled and installed the 2.6.32.7 kernel from [www.kernel.org](www.kernel.org) which is probably why it worked as is.

---

### Post by jimbob on 2010-03-12
> hey I don't know if anyone else knows this but just adding :
blacklist rt2800usb
to /etc/modprobe.d/blacklist.conf and rebooting makes it work!

  Were you able to use WPA2 security also or is your AP unsecured?

---

### Post by sandy8925 on 2010-03-20
Yes I AM using it with WPA2. Works well without any problems.

---

### Post by jimbob on 2010-03-27
> Yes I AM using it with WPA2. Works well without any problems.
Wish I could report the same.  I downloaded and installed Lucid Beta 1 with kernel 2.6.32-16-generic to see if I could get it to run.After blacklisting rt2800usb I was able to see my and my neighbor's APs and the green light was working just fine; however I was not able to associate with my own AP which uses WPA2.  I suspect it has something to do with the supplicant but can't be sure.  So we're not quite there yet IMHO.  I may put it on my laptop and head over to the library later today to see if it will work with no security.  Can't try that here as too many people in the house use WPA2 on this router.

EDIT:  "Out of the box" Lucid with kernel 2.6.32-16 works fine with unsecured AP at our local library but fails when trying to connect to WPA2 secured locations.  This leads me to suspect wpa-supplicant or the links thereto.

---

### Post by Taemojitsu on 2010-05-11
This is somewhat fixed in Lucid using wireless backports, but I haven't tried an encrypted connection.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446889](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446889)

---

### Post by thermoblu2 on 2010-06-08
what version driver do i need to get to make the airodump-ng to pick up networks or do you know if the airplay works with usb adapters ?

---

### Post by Kjeldgaard on 2010-08-14
> **jimbob said:**
> Wish I could report the same.  I downloaded and installed Lucid Beta 1 with kernel 2.6.32-16-generic to see if I could get it to run.After blacklisting rt2800usb I was able to see my and my neighbor's APs and the green light was working just fine; however I was not able to associate with my own AP which uses WPA2.  I suspect it has something to do with the supplicant but can't be sure.  So we're not quite there yet IMHO.  I may put it on my laptop and head over to the library later today to see if it will work with no security.  Can't try that here as too many people in the house use WPA2 on this router.

EDIT:  "Out of the box" Lucid with kernel 2.6.32-16 works fine with unsecured AP at our local library but fails when trying to connect to WPA2 secured locations.  This leads me to suspect wpa-supplicant or the links thereto.

After avoiding installing 10.04 for some month because I didn't have any problems with the 9.10 version, I recently installed the 10.04. And it was very easy to get the wireless dongle working. I just blacklisted the rt2800usb and all wireless networks was shown. But first I couldn't connect to my own wpa2 secured AP, just as you couldn't. Then I read a post (can't remember where) which said that encryption should be aes and NOT aes+tkip. I changed the encryption type in my wireless router, connected to my AP and it have been working perfect ever since.

Try change the encryption type in your wireless router and it will hopefully work. I don't know the strength of the aes encryption vs. aes+tkip encryption

---

### Post by jimbob on 2010-08-14
@Kjeldgaard, you are a genius!  I went into my router and changed the setting from AES+TKIP to AES, then blacklisted rt2800usb, rebooted and it came up immediately.  It has been running continuously on the Reuters News Videos without a problem for 2 hours now.

There is an ongoing bug #446889 in Launchpad all about the WUSB54GC dongle that I am going to post this solution on if you don't mind so others can try it to verify our results.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446889](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446889)

---

### Post by bkratz on 2010-08-14
> **jimbob said:**
> @Kjeldgaard, you are a genius!  I went into my router and changed the setting from AES+TKIP to AES, then blacklisted rt2800usb, rebooted and it came up immediately.  It has been running continuously on the Reuters News Videos without a problem for 2 hours now.

There is an ongoing bug #446889 in Launchpad all about the WUSB54GC dongle that I am going to post this solution on if you don't mind so others can try it to verify our results.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446889](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446889)

See post #65 of that bug report

---

### Post by jimbob on 2010-08-14
> See post #65 of that bug report
Guess that's the one Kjeldgaard was referring to:
> Then I read a post (can't remember where) which said that encryption should be aes and NOT aes+tkip.
I'm sure I tried that at one time or another over the many months I (and others) have tried to get this thing to work but I guess I never had quite the right combination at any one time.

---

### Post by Kjeldgaard on 2010-08-28
Glad I could help you with this problem.

Read up on the tkip and aes issue. And when you select aes you lose some backward compatibility. Some old network devices require the aes+tkip encryption. The encryption strength is the same.

---

### Post by dalaj on 2010-08-28
Hello,

  If you have come to this forum for help like me and are going to compile the RT2870STA module according to one of the given procedures or you are not satisfied with such solution, I recommend to read this notable Flash63's post on [http://ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://ubuntuforums.org/showpost.php?p=8591348&postcount=6) first. Maybe somebody has already mentioned it here but it does not seem so.

  The problem of my dongle (SMCWUSBS-N3 with Ralink 3070 chipset, ID 083a:a701) probably was not having been recognized by the module, as "083ApA701" was not contained in the output of modinfo rt2870sta. Today the procedure proposed by Flash63 made it work within 4 bash lines + a modification of /etc/modules, no compiling!
  Beside that I have made several other changes: 

[LIST=1] 
[*]Blacklisted those possibly conflicting modules. 
[*]Uninstalled all Network Manager packages and installed WICD. 
[*]Installed linux-backports-modules-wirelles-lucid-generic(I specfically used the ones with -pae extension, believing it suits my -pae kernel) and linux-backports-modules-headers-lucid-generic(-pae). 
[/LIST]
 
  I cannot confirm that all of these additional steps were necessary, but when I tried the procedure with the Network Manager, the driver was there, the wlan0 interface was created, I could scan for the networks but never connected (WPA2/PSK, SSID broadcast), the network manager claimed incorrect password which I bet was correct. But WICD did it. Also upon uninstallation of the backported packages i was unable to connect again (incorrect password). So I returned to the backported packages.
There is still an issue with the stability of the connection. After some time (usually minutes) I realize that I have been disconnected. I do not know yet, whether the cause lies in instability of the signal (I am less then 6 m from the WiFi router now, behind ca. 55 cm of bricks, WICD displays signal level 35-50 %). When I have time, I will experiment with positioning and antennas orientation to get closer to be sure the issue is not in instability of the WiFi signal.  Finally I would like to thank all those who have helped with this forum and other ones too, namely Radixor, B K chili 555 and Flash 63 of course), without you I would be lost and probably have to resort to buying a self-standing WiFi client connected via Ethernet - which in the end I may buy anyway, to be sure that my mother gets a good and stable connection. But I am definitely feeling much better when the damned USB thing finally does something.

---

### Post by rightkick on 2010-11-08
I tried to follow the steps to install Linksys WUSB54GV v3 USB adapter but it fails when i run "make".

The message i get is:

```
make -C tools
make[1]: Entering directory `/home/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
/home/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.30.9/build SUBDIRS=/home/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-source-2.6.30.9'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.30.9/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.o
make[1]: Leaving directory `/usr/src/linux-source-2.6.30.9'
error 2
```I ran all commands as root. I read the other posts and messed around but still encountering this problem. Can anybody point me any direction? Thanx

---

### Post by chili555 on 2010-11-08
> [COLOR="Red"]2008[/COLOR]_0[COLOR="Red"]925[/COLOR]_RT2870_Linux_STA_v1.4.0.0Man, that is an old-timer! I suspect it's a few generations too old for the current kernel.

rt2870sta is built-in to the current kernel. Doesn't it work for you? Please post:```
lsusb
```Thanks.

---

### Post by rightkick on 2010-11-08
thank you for your quick reply!
You're right. That's an old driver. I downloaded the latest one (2010_0709_RT2870_Linux_STA_v2.4.0.1) and installed it successfully without any errors during "make" and "make install". I followed the rest steps (insmod, ...) but the card doesn't show when i run ifconfig -a. I added also at /etc/netwok/interfaces a row with the lines:  

auto ra0
iface ra0 inet dhcp

although it did already have a similar line with wlan0.

After the reboot the module rt2870sta.ko didn't show when i ran "lsmod | grep 'rt2870*'", so i installed it with "insmod /lib/.../rt2870sta.ko" to no avail -> the usb antenna still not appearing.

I'm installing it on Backtrack4 (Ubuntu based), on a virtual machine. I ran "start-network" to start the network. I tried even "/etc/init.d/networking stop/start" but the problem remained.

(I did try to install the already existing module inside the OS but the usb antenna didn't show. So i tried to install a new driver from Ralink website)

When running **lsusb** i get:

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 090c:1000 Feiya Technology Corp. Flash Drive
**Bus 001 Device 002: ID 1737:0077 Linksys **
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


What else can i do?
Thank you.

---

### Post by chili555 on 2010-11-08
Let's have a look at:```
dmesg | grep rt2
```May I assume Backtrack4 doesn't use Network Manager?

---

### Post by rightkick on 2010-11-08
i get nothing when issuing:

```
dmesg | grep rt2
```but i get a lot of seeminlgy unrelated messages when i run:

```
dmesg | grep rt2*

output:

KERNEL supported cpus:
Movable zone start PFN for each node
ACPI: PM-Timer IO Port: 0x1008
Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
Enabling unmasked SIMD FPU exception support... done.
virtual kernel memory layout:
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
ACPI: (supports S0 S1 S4 S5)
pci 0000:00:07.1: reg 20 io port: [0x10c0-0x10cf]
pci 0000:00:07.7: reg 10 io port: [0x1080-0x10bf]
pci 0000:00:0f.0: reg 10 io port: [0x10d0-0x10df]
pci 0000:00:10.0: reg 10 io port: [0x1400-0x14ff]
pci 0000:00:15.0: PME# supported from D0 D3hot D3cold
pci 0000:00:15.1: PME# supported from D0 D3hot D3cold
pci 0000:00:15.2: PME# supported from D0 D3hot D3cold
pci 0000:00:15.3: PME# supported from D0 D3hot D3cold
pci 0000:00:15.4: PME# supported from D0 D3hot D3cold
pci 0000:00:15.5: PME# supported from D0 D3hot D3cold
pci 0000:00:15.6: PME# supported from D0 D3hot D3cold
pci 0000:00:15.7: PME# supported from D0 D3hot D3cold
pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
pci 0000:00:16.1: PME# supported from D0 D3hot D3cold
pci 0000:00:16.2: PME# supported from D0 D3hot D3cold
pci 0000:00:16.3: PME# supported from D0 D3hot D3cold
pci 0000:00:16.4: PME# supported from D0 D3hot D3cold
pci 0000:00:16.5: PME# supported from D0 D3hot D3cold
pci 0000:00:16.6: PME# supported from D0 D3hot D3cold
pci 0000:00:16.7: PME# supported from D0 D3hot D3cold
pci 0000:00:17.0: PME# supported from D0 D3hot D3cold
pci 0000:00:17.1: PME# supported from D0 D3hot D3cold
pci 0000:00:17.2: PME# supported from D0 D3hot D3cold
pci 0000:00:17.3: PME# supported from D0 D3hot D3cold
pci 0000:00:17.4: PME# supported from D0 D3hot D3cold
pci 0000:00:17.5: PME# supported from D0 D3hot D3cold
pci 0000:00:17.6: PME# supported from D0 D3hot D3cold
pci 0000:00:17.7: PME# supported from D0 D3hot D3cold
pci 0000:00:18.0: PME# supported from D0 D3hot D3cold
pci 0000:00:18.1: PME# supported from D0 D3hot D3cold
pci 0000:00:18.2: PME# supported from D0 D3hot D3cold
pci 0000:00:18.3: PME# supported from D0 D3hot D3cold
pci 0000:00:18.4: PME# supported from D0 D3hot D3cold
pci 0000:00:18.5: PME# supported from D0 D3hot D3cold
pci 0000:00:18.6: PME# supported from D0 D3hot D3cold
pci 0000:00:18.7: PME# supported from D0 D3hot D3cold
pci 0000:02:00.0: reg 20 io port: [0x20c0-0x20df]
pci 0000:02:01.0: reg 10 io port: [0x2080-0x20bf]
pci 0000:02:04.0: reg 10 io port: [0x2000-0x207f]
pci 0000:00:11.0: bridge io port: [0x2000-0x3fff]
pci 0000:00:15.0: bridge io port: [0x4000-0x4fff]
pci 0000:00:15.1: bridge io port: [0x8000-0x8fff]
pci 0000:00:15.2: bridge io port: [0xc000-0xcfff]
pci 0000:00:16.0: bridge io port: [0x5000-0x5fff]
pci 0000:00:16.1: bridge io port: [0x9000-0x9fff]
pci 0000:00:16.2: bridge io port: [0xd000-0xdfff]
pci 0000:00:17.0: bridge io port: [0x6000-0x6fff]
pci 0000:00:17.1: bridge io port: [0xa000-0xafff]
pci 0000:00:17.2: bridge io port: [0xe000-0xefff]
pci 0000:00:18.0: bridge io port: [0x7000-0x7fff]
pci 0000:00:18.1: bridge io port: [0xb000-0xbfff]
pci 0000:00:18.2: bridge io port: [0xf000-0xffff]
system 00:01: ioport range 0x1000-0x103f has been reserved
system 00:01: ioport range 0x1040-0x104f has been reserved
system 00:01: ioport range 0xcf0-0xcf1 has been reserved
system 00:0c: ioport range 0x1060-0x107f has been reserved
pcieport-driver 0000:00:15.0: irq 24 for MSI/MSI-X
pcieport-driver 0000:00:15.0: setting latency timer to 64
pcieport-driver 0000:00:15.1: irq 25 for MSI/MSI-X
pcieport-driver 0000:00:15.1: setting latency timer to 64
pcieport-driver 0000:00:15.2: irq 26 for MSI/MSI-X
pcieport-driver 0000:00:15.2: setting latency timer to 64
pcieport-driver 0000:00:15.3: irq 27 for MSI/MSI-X
pcieport-driver 0000:00:15.3: setting latency timer to 64
pcieport-driver 0000:00:15.4: irq 28 for MSI/MSI-X
pcieport-driver 0000:00:15.4: setting latency timer to 64
pcieport-driver 0000:00:15.5: irq 29 for MSI/MSI-X
pcieport-driver 0000:00:15.5: setting latency timer to 64
pcieport-driver 0000:00:15.6: irq 30 for MSI/MSI-X
pcieport-driver 0000:00:15.6: setting latency timer to 64
pcieport-driver 0000:00:15.7: irq 31 for MSI/MSI-X
pcieport-driver 0000:00:15.7: setting latency timer to 64
pcieport-driver 0000:00:16.0: irq 32 for MSI/MSI-X
pcieport-driver 0000:00:16.0: setting latency timer to 64
pcieport-driver 0000:00:16.1: irq 33 for MSI/MSI-X
pcieport-driver 0000:00:16.1: setting latency timer to 64
pcieport-driver 0000:00:16.2: irq 34 for MSI/MSI-X
pcieport-driver 0000:00:16.2: setting latency timer to 64
pcieport-driver 0000:00:16.3: irq 35 for MSI/MSI-X
pcieport-driver 0000:00:16.3: setting latency timer to 64
pcieport-driver 0000:00:16.4: irq 36 for MSI/MSI-X
pcieport-driver 0000:00:16.4: setting latency timer to 64
pcieport-driver 0000:00:16.5: irq 37 for MSI/MSI-X
pcieport-driver 0000:00:16.5: setting latency timer to 64
pcieport-driver 0000:00:16.6: irq 38 for MSI/MSI-X
pcieport-driver 0000:00:16.6: setting latency timer to 64
pcieport-driver 0000:00:16.7: irq 39 for MSI/MSI-X
pcieport-driver 0000:00:16.7: setting latency timer to 64
pcieport-driver 0000:00:17.0: irq 40 for MSI/MSI-X
pcieport-driver 0000:00:17.0: setting latency timer to 64
pcieport-driver 0000:00:17.1: irq 41 for MSI/MSI-X
pcieport-driver 0000:00:17.1: setting latency timer to 64
pcieport-driver 0000:00:17.2: irq 42 for MSI/MSI-X
pcieport-driver 0000:00:17.2: setting latency timer to 64
pcieport-driver 0000:00:17.3: irq 43 for MSI/MSI-X
pcieport-driver 0000:00:17.3: setting latency timer to 64
pcieport-driver 0000:00:17.4: irq 44 for MSI/MSI-X
pcieport-driver 0000:00:17.4: setting latency timer to 64
pcieport-driver 0000:00:17.5: irq 45 for MSI/MSI-X
pcieport-driver 0000:00:17.5: setting latency timer to 64
pcieport-driver 0000:00:17.6: irq 46 for MSI/MSI-X
pcieport-driver 0000:00:17.6: setting latency timer to 64
pcieport-driver 0000:00:17.7: irq 47 for MSI/MSI-X
pcieport-driver 0000:00:17.7: setting latency timer to 64
pcieport-driver 0000:00:18.0: irq 48 for MSI/MSI-X
pcieport-driver 0000:00:18.0: setting latency timer to 64
pcieport-driver 0000:00:18.1: irq 49 for MSI/MSI-X
pcieport-driver 0000:00:18.1: setting latency timer to 64
pcieport-driver 0000:00:18.2: irq 50 for MSI/MSI-X
pcieport-driver 0000:00:18.2: setting latency timer to 64
pcieport-driver 0000:00:18.3: irq 51 for MSI/MSI-X
pcieport-driver 0000:00:18.3: setting latency timer to 64
pcieport-driver 0000:00:18.4: irq 52 for MSI/MSI-X
pcieport-driver 0000:00:18.4: setting latency timer to 64
pcieport-driver 0000:00:18.5: irq 53 for MSI/MSI-X
pcieport-driver 0000:00:18.5: setting latency timer to 64
pcieport-driver 0000:00:18.6: irq 54 for MSI/MSI-X
pcieport-driver 0000:00:18.6: setting latency timer to 64
pcieport-driver 0000:00:18.7: irq 55 for MSI/MSI-X
pcieport-driver 0000:00:18.7: setting latency timer to 64
ACPI: Processor [CPU0] (supports 8 throttling states)
Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
piix 0000:00:07.1: IDE port disabled
hda: VMware Virtual IDE CDROM Drive, ATAPI CD/DVD-ROM drive
ide_generic: please use "probe_mask=0x3f" module parameter for probing all legacy ISA IDE ports
Loading iSCSI transport class v2.0-870.
iscsi: registered transport (tcp)
iscsi: registered transport (qla4xxx)
       with "disable_clustering=1" and report to maintainers
scsi2 : ioc0: LSI53C1030 B0, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=17
scsi 2:0:0:0: Direct-Access     VMware,  VMware Virtual S 1.0  PQ: 0 ANSI: 2
ehci_hcd 0000:02:02.0: cache line size of 128 is not supported
ehci_hcd 0000:02:02.0: USB 2.0 started, EHCI 1.00
hub 1-0:1.0: 6 ports detected
hub 2-0:1.0: 2 ports detected
USB Mass Storage support registered.
serio: i8042 KBD port at 0x60,0x64 irq 1
serio: i8042 AUX port at 0x60,0x64 irq 12
RPC: Registered udp transport module.
RPC: Registered tcp transport module.
Using IPI No-Shortcut mode
PM: Starting manual resume from disk
kjournald starting.  Commit interval 5 seconds
udevd version 124 started
Linux agpgart interface v0.103
agpgart-intel 0000:00:00.0: Intel 440BX Chipset
agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x0
rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
rtc0: alarms up to one month, y3k, 114 bytes nvram
parport_pc 00:08: reported by Plug and Play ACPI
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
lp0: using parport0 (interrupt-driven).
```

I'm new in Ubuntu and Backtrack4. Backtrack as far as i know uses a script-like network manager (start-network) and a gui to check the wireless network.

---

### Post by chili555 on 2010-11-08
What kernel version do you use?```
uname -r
```Please try:```
sudo modprobe rt2870sta
dmesg | grep rt2
iwconfig
```Thanks.

---

### Post by rightkick on 2010-11-08
kernel is: 2.6.30.9

now dmesg gives: usbcore: registered new interface driver rt2870

and iwconfig gives: 

lo     no wireless extensions.
eth0 no wireless extensions.

---

### Post by chili555 on 2010-11-08
That's a pretty old kernel, too! I wonder if it recognizes your device. Maybe we can "adjust" it. Please post:```
modinfo rt2870sta | grep 0077
```

---

### Post by rightkick on 2010-11-08
I get nothing when i run modinfo rt2870sta | grep 0077

but here is the full modinfo without grep:
```

filename:       /lib/modules/2.6.30.9/kernel/drivers/net/wireless/rt2870sta.ko
version:        2.4.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     5598BFE60F8B720D8D64062
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.30.9 SMP mod_unload 686 
parm:           mac:rt28xx: wireless mac addr (charp)
```

---

### Post by chili555 on 2010-11-09
Let's see if we can adjust it. Remove the device and then please do:```
cd drivers/2010_0709_RT2870_Linux_STA_v2.4.0.1
```Substitute the location of the file you downloaded. Now do:```
make clean
sudo make uninstall
gedit common/rtusb_dev_id.c
```Add a line as follows in the string of usb.ids:```
{USB_DEVICE{0x1737,0x0077}}, /*Linksys*/
```When you have done it correctly, it will look like the attached. I have attached only the relevant section, not the entire file. It doesn't matter whether the added line is first, second or otherwise. Be sure the indentations, etc. are exact. Proofread carefully, save and close gedit. Now do:```
make
sudo make install
```Are there any errors? If not, please reinsert the device and do:```
sudo modprobe rt2870sta
```Does your device come to life?

---

### Post by rightkick on 2010-11-09
After upgrading to kernel 2.6.34 and following your instructions (without encountering any errors) the LED of the USB antenna is flashing green! Thats a great success! Thank you very much for your help and this beautiful forum! I was searching in which header file to put that line of device ID. Thank you for pointing me there!

But it seems that the card is simply live but cannot detect any wireless connections.

I put the module inside /etc/modules to load automatically on each reboot.

Also I did:

**ifconfig ra0 up**


and started graphicaly wicd (network manager) where it stated that no wireless connections detected. I'm sure I have at least for of them here, and one of them I'm using for my Windows PC.

**iwconfig** gives me rightly:
lo    no wireless connection
ra0  Ralink STA

Any thoughts on this?
Thanks again a bunch!

---

### Post by chili555 on 2010-11-09
It would be helpful to see the entirety of:```
iwconfig ra0
sudo iwlist ra0 scan
```Thanks.

If you upgraded the kernel, we might now be able to get the built-in to work, but let's take one step at a time.

---

### Post by rightkick on 2010-11-09
The outputs of the commands are like this:[B]

iwconfig ra0[/B]:

```
ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```**sudo iwlist ra0 scan**:

```
ra0       No scan results
```

---

### Post by chili555 on 2010-11-09
Can you confirm that, before you compiled, you made these changes outlined in the README_STA?> 3> In os/linux/config.mk 
** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.If not, please make the changes now, remove the device and re-compile:```
cd drivers/2010_0709_RT2870_Linux_STA_v2.4.0.1
make clean
make
sudo make install
```Reinsert the device and post back with your report. We will be interested in:```
sudo iwlist ra0 scan
dmesg | grep -i rt2
```

---

### Post by rightkick on 2010-11-09
I followed the previous steps, but did try also to install the driver onto a clean intalled Backtrack System with kernel 2.6.34, having the same results.

The steps i did in particular:

```
1. Disconnected device
2. Set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y' inside os/linux/config.mk file.
3. Set {USB_DEVICE{0x1737,0x0077}}, /*Linksys*/ inside common/rtusb_dev_id.c file.
4. make
5. sudo make install
6. Connected device
7. sudo modprobe rt2870sta
8. Blacklisted rt2800usb that I noticed was automatically loading.
9. Put rt2870sta in /etc/modules to autoload on reboot.
10. reboot
11. start-network
12. ifconfig ra0 up (only here the dongle is alive and the LED flashes)
```The output from **sudo iwlist ra0 scan**:
```
ra0       No scan results
```The output from **dmesg | grep -i rt2**:
```
Compaq SMART2 Driver (v 2.6.0)
usbcore: registered new interface driver rt2870
<==== rt28xx_init, Status=0
```

---

### Post by chili555 on 2010-11-09
rt2800usb has some dependencies:```
modinfo rt2800usb
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     78DA166470C3E90F51592AF
--- snip ---
[COLOR="Red"]depends:        rt2800lib,rt2x00usb,crc-ccitt[/COLOR]
vermagic:       2.6.35-22-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)

```Are those loading? You need to blacklist them, too, if so.

---

### Post by rightkick on 2010-11-10
No, the dependencies are not loading although i didn't blacklist them.
The output from lsmod | grep rt2*
```
gameport                6725  1 snd_ens1371
rt2870sta             537431  0 
parport_pc             18091  1 
parport                24463  2 lp,parport_pc
rtc_cmos                7678  0 
rtc_core               11351  1 rtc_cmos
rtc_lib                 1526  1 rtc_core
agpgart                22417  1 intel_agp
```The dependencies for my rt2800usb are
```
filename:       /lib/modules/2.6.34/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     7E5546053A053BA6DC87CE4
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
...
depends:        rt2800lib,rt2x00usb
vermagic:       2.6.34 SMP mod_unload CORE2 
parm:           nohwcrypt:Disable hardware encryption. (bool)
```and lsmod | grep crc* gives nothing and lsmod | grep rt28* gives only rt2870sta.

---

### Post by chili555 on 2010-11-10
Please check:```
modinfo rt2870sta
```My stock not-compiled version says:> modinfo rt2870sta
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
description:    RT2870/RT3070 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
[COLOR="Red"]firmware:       rt3071.bin
firmware:       rt3070.bin
firmware:       rt2870.bin[/COLOR]
srcversion:     93E93E3E336F412601AF0FA
--- snip ---
[COLOR="Red"]depends:        crc-ccitt[/COLOR]
staging:        Y
vermagic:       2.6.35-22-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)Does your compiled version require firmware? Does it depend on crc-ccitt which is evidently not loaded? Please check for these firmwares in /lib/firmware; I will send them to you if they are required according to *modinfo*.

---

### Post by rightkick on 2010-11-10
Doing **modinfo rt2870sta** on a built-in not-compiled module on a clean backtrack system i get the same results as when i issue this command after  i have compiled and installed the downloaded one. No dependencies, no firmware!
In the second case, before installing the driver, i renamed to rt2870sta.ko.old the existing (built in) one to ensure i will have the new module installed and loaded.
And when i issued** find /* -name crc-ccitt** i got nothing.

```
filename:       /lib/modules/2.6.34/kernel/drivers/net/wireless/rt2870sta.ko
version:        2.4.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     F16FD4DF757233C4246A85A
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.34 SMP mod_unload CORE2 
parm:           mac:rt28xx: wireless mac addr (charp)
```

---

### Post by chili555 on 2010-11-10
Do you see anything interesting in:```
dmesg | grep -i rt2
sudo cat /var/log/syslog | grep -i rt2
sudo cat /var/log/syslog | grep ra0
```I downloaded BT4r1 and ran the live CD for a while. I believe it uses Wicd.

Please post anything you think is significant.

---

### Post by rightkick on 2010-11-11
I managed to install the WUSB54GCv3 dongle by installing rt3070 driver, with all the tweaks inside the files config.mk and rtusb_dev_id.c the same as previously.
From the command** iwlist ra0 scan** i see now all the wireless networks as expected, although sometimes it doesn't find any.

when compiling the drivers i noticed a warning:

```
make -C tools
make[1]: Entering directory `/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/tools'
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/tools/bin2h
cp -f os/linux/Makefile.6 /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/Makefile
make -C /lib/modules/2.6.34/build SUBDIRS=/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/li
nux modules
make[1]: Entering directory `/usr/src/linux-source-2.6.34'

  [COLOR=Red]WARNING: Symbol version dump /usr/src/linux-source-2.6.34/Module.symvers
           is missing; modules will have no dependencies and modversions.[/COLOR]

  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/crypt_md5.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/crypt_sha2.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/crypt_hmac.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/crypt_aes.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/crypt_arc4.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/mlme.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_wep.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/action.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_data.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/rtmp_init.o
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/rtmp_init.c: In function
'RTMPReadChannelPwr':
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/rtmp_init.c:555: warning:
 unused variable 'Tx1FinePowerCtrl'
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/rtmp_init.c:555: warning:
 unused variable 'Tx0FinePowerCtrl'
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/rtmp_init.c:555: warning:
 unused variable 'Tx1ALC'
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/rtmp_init.c:555: warning:
 unused variable 'Tx0ALC'
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_tkip.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_aes.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_sync.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/eeprom.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_sanity.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_info.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_cfg.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_wpa.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/dfs.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/spectrum.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/rtmp_timer.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/rt_channel.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_profile.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_asic.o
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_asic.c: In function '
InitDesiredTSSITable':
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_asic.c:1521: warning:
 missing braces around initializer
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_asic.c:1521: warning:
 (near initialization for 'BbpR49.field')
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_asic.c:1525: warning:
 missing braces around initializer
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_asic.c:1525: warning:
 (near initialization for 'TxPwrOffset.field')
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_asic.c:1523: warning:
 unused variable 'Tx0PowerSetting'
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_cmd.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../sta/assoc.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../sta/auth.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../sta/auth_rsp.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../sta/sync.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../sta/sanity.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../sta/rtmp_data.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../sta/connect.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../sta/wpa.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../sta/ags.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../sta/sta_cfg.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../os/linux/rt_profile.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../os/linux/rt_linux.o
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../os/linux/rt_linux.c: In function
 'RtmpOSNetDevDetach':
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../os/linux/rt_linux.c:1700: warnin
g: initialization discards qualifiers from pointer target type
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../os/linux/rt_linux.c: In function
 'RtmpOSNetDevAttach':
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../os/linux/rt_linux.c:1737: warnin
g: initialization discards qualifiers from pointer target type
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../os/linux/rt_main_dev.o
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../os/linux/rt_main_dev.c: In funct
ion 'MainVirtualIF_close':
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../os/linux/rt_main_dev.c:123: warn
ing: unused variable 'Cancelled'
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/ba_action.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_mac_usb.o
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_mac_usb.c: In functio
n 'NICInitTransmit':
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_mac_usb.c:849: warnin
g: passing argument 3 of 'RTMPAllocUsbBulkBufStruct' from incompatible pointer type
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_mac_usb.c:932: warnin
g: passing argument 3 of 'RTMPAllocUsbBulkBufStruct' from incompatible pointer type
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_mac_usb.c:949: warnin
g: passing argument 3 of 'RTMPAllocUsbBulkBufStruct' from incompatible pointer type
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_mac_usb.c:975: warnin
g: passing argument 3 of 'RTMPFreeUsbBulkBufStruct' from incompatible pointer type
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_mac_usb.c:982: warnin
g: passing argument 3 of 'RTMPFreeUsbBulkBufStruct' from incompatible pointer type
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_mac_usb.c:997: warnin
g: passing argument 3 of 'RTMPFreeUsbBulkBufStruct' from incompatible pointer type
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_mac_usb.c:1015: warni
ng: passing argument 3 of 'RTMPFreeUsbBulkBufStruct' from incompatible pointer type
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_mac_usb.c: In functio
n 'RTMPFreeTxRxRingMemory':
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_mac_usb.c:1150: warni
ng: passing argument 3 of 'RTMPFreeUsbBulkBufStruct' from incompatible pointer type
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_mac_usb.c:1157: warni
ng: passing argument 3 of 'RTMPFreeUsbBulkBufStruct' from incompatible pointer type
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_mac_usb.c:1194: warni
ng: passing argument 3 of 'RTMPFreeUsbBulkBufStruct' from incompatible pointer type
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/rtusb_io.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/rtusb_bulk.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/rtusb_data.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/cmm_data_usb.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/ee_prom.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/ee_efuse.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/rtmp_mcu.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/rt_rf.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../chips/rt3070.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../chips/rt30xx.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../chips/rt33xx.o
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../chips/rt33xx.c: In function 'RT3              3xxSetRxAnt':
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../chips/rt33xx.c:107: warning: unu              sed variable 'x'
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../chips/rt3370.o
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../chips/rt3370.c: In function 'NIC              InitRT3370RFRegisters':
/usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../chips/rt3370.c:59: warning: unus              ed variable 'bbpreg'
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/rtusb_dev_id.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../os/linux/rt_usb.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../os/linux/rt_usb_util.o
  CC [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../os/linux/usb_main_dev.              o
  LD [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/rt3370sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/rt3370sta.mod.o
  LD [M]  /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/rt3370sta.ko
make[1]: Leaving directory `/usr/src/linux-source-2.6.34'
cp -f /usr/src/drivers/Linksys/DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/rt3370sta.ko /tftpboot
```The driver seems to work, although it assumes only 1MB/s. the output of** iwconfig ra0** is:

```
ra0       Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Monitor  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=100/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```Unfortunately this version (version 3) of the USB dongle doesn't support packet injection, or i don't know any enhanced driver for this device that enables this feature. I bought it thinking that was going to be version 1 (silk color) and it turned out to be the black one. I hope i can return it or find a card that supports packet injection. If someone knows any way to make this dongle able to inject packets i will be glad to hear.

@chilli555: many thanks for your support!

---


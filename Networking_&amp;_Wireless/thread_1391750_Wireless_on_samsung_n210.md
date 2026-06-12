---
title: "Wireless on samsung n210"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by johnmollaghan on 2010-01-27
Just installed Netbook Remix on a Samsung N210.

No wireless networks are being detected, what do I need to install to get this working? 

Thanks

---

### Post by chili555 on 2010-01-27
Please open a terminal and do:```
lspci -nn | grep Network
sudo lshw -C network
```Please post the result and we'll help you.

---

### Post by suffice on 2010-01-27
I am also having the same problem with an N210.... here is the output for this one. Before stumbling upon this post I did more or less those comdands and guessed that the UNCLAIMED network is the one I'm lookin for.  Then searched and here I am.


lspci -nn | grep Network..

05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8192] (rev 01)

and
*-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 00
       serial: 00:24:54:40:cc:58
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=(blanked_out_for_post) latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:f0200000-f0203fff ioport:3000(size=256

---

### Post by chili555 on 2010-01-27
> Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [[COLOR="Red"]10ec:8192[/COLOR]] (rev 01)For this device only; I don't know yet if johnmollaghan has the same.

Download the driver here: [http://rs110.rapidshare.com/files/336365402/rtl8192e_linux_2.6.0011.1029.2009.tar.gz](http://rs110.rapidshare.com/files/336365402/rtl8192e_linux_2.6.0011.1029.2009.tar.gz)

Open a terminal and do:```
sudo apt-get install linux-headers-`uname -r` build-essential
```Those little tick marks are on my US keyboard along with ~.

By default, in Firefox, downloads go to the Desktop. Right-click the .tar.gz file and select 'Extract here.' A folder will be created called 'rtl8192e-blah-blah' Open a terminal and do:```
cd Desktop/rtl8
```Press the Tab key and the rest will be filled in for you. Press Enter. Then do:```
make
sudo su
make install
modprobe r8192e-pci
iwconfig
```Do you now have a wireless interface? Can you click Network Manager and connect?

Please post back any difficulties or errors.

---

### Post by suffice on 2010-01-27
I will check it out when I'm home from work today.   Thanks a bunch.

---

### Post by hamstah on 2010-01-30
Hi,

Just received my n210 this morning and ran into the same problem as you. Thank you very much chili555 for your help, it worked almost instantly.

I didnt have to install build-essential or linux-headersm but I did have to install linux-source to solve a problem described here [http://ubuntuforums.org/showthread.php?t=1047374]("http://ubuntuforums.org/showthread.php?t=1047374").

The rest worked fine. 
Don't use sudo for the make install as it won't use linux-source as needed.

Hope this helps

---

### Post by donmatas on 2010-02-08
Does works with UNR 9.10?

---

### Post by lucas.andion on 2010-02-09
The Wireless LAN is working for me with a fresh installation of UNR on my N210

---

### Post by donmatas on 2010-02-09
> **lucas.andion said:**
> The Wireless LAN is working for me with a fresh installation of UNR on my N210

thank you very much.
Do you have any other problem with it? I have heard that there's an issue with the brightness and the cam...

saludos
DM

---

### Post by calyth on 2010-02-15
Beware that the alpha drivers (from the rapidshare link) will probably b0rk suspend and hibernate.
I've no problems going to Samsung's site, download the WinXP drivers, and use NDIS wrapper - that won't kill the suspend and hibernate.

---

### Post by northd_tech on 2010-02-15
If you email Realtek, they will email you a newer version of that driver.  I haven't had access to the computer that I'm trying to fix for a week or so, but I got the driver from Kidman, and they are usually pretty fast on the response time.

If you search the forum for "realtek 8192e" you should find a couple of threads where I've been posting my long-standing struggle with this Realtek card- 64-bit can be a real pain!

I couldn't get the first 1 or 2 versions of that sourcecode tarball to work under 64-bit, but it sounds like this new file "rtl8192e_linux_2.6.0013.0127.2010.tar.gz" is the "good stuff" from what I've read here.  I've got a copy on my hard disk, but Realtek doesn't have a direct download link that I'm aware of (email only).

Realtek may have a newer version than that by now, too.

---

### Post by lucas.andion on 2010-02-15
> **donmatas said:**
> 
Do you have any other problem with it? I have heard that there's an issue with the brightness and the cam...
DM


[LIST]
[*]Brightness fn Keys are not working for me. The only fn keys that work for me are the sound-related ones.
[/LIST]

[LIST]
[*]Webcam is working for me.
[/LIST]
The same working conditions apply on Moblin 2.1 with a fresh install: wireless working & some fn keys not working.

---

### Post by donmatas on 2010-02-15
> **lucas.andion said:**
> [LIST]
[*]Brightness fn Keys are not working for me. The only fn keys that work for me are the sound-related ones.
[/LIST]

[LIST]
[*]Webcam is working for me.
[/LIST]
The same working conditions apply on Moblin 2.1 with a fresh install: wireless working & some fn keys not working.

thanks!

---

### Post by johnmollaghan on 2010-02-16
Sorry for the delay in getting back to you.That worked perfectly! I had to reboot in order to see the networks.

---

### Post by JaffaTheCake on 2010-02-25
Is there any way of tracking the issues with UNR and the Samsung n210/220? I'd like to switch to UNR once the hardware is supported.

---

### Post by donmatas on 2010-02-25
> **JaffaTheCake said:**
> Is there any way of tracking the issues with UNR and the Samsung n210/220? I'd like to switch to UNR once the hardware is supported.

I have installed on My wife's netbook. It is working very well except for:

the brightness it's allways at the lower status. It's supposed to be fixed in the new Kernell

the ctrl key doesn't work for combinations like "copy" (ctrl+c), "paste" (ctrl+v), "open a new tab" (ctrl+t) or "hide folder" (ctrl+h).

Even with this issues, it works a lot better than win 7

saludos
DM

---

### Post by JaffaTheCake on 2010-02-26
I couldn't find tickets for those issues, are there any you know of. I make extensive use of copy & paste, brightness & hibernate so can't really switch until they're working.

Is Wi-fi working now then?

---

### Post by donmatas on 2010-02-27
> **JaffaTheCake said:**
> I couldn't find tickets for those issues, are there any you know of. I make extensive use of copy & paste, brightness & hibernate so can't really switch until they're working.

Is Wi-fi working now then?

Jaffa: Hibernation works perfectly

wait a couple of weeks for the new kernell for solving the brightness control issue

saludos
M

---

### Post by donmatas on 2010-03-15
> **donmatas said:**
> I have installed on My wife's netbook. It is working very well except for:

the brightness it's allways at the lower status. It's supposed to be fixed in the new Kernell

the ctrl key doesn't work for combinations like "copy" (ctrl+c), "paste" (ctrl+v), "open a new tab" (ctrl+t) or "hide folder" (ctrl+h).

Even with this issues, it works a lot better than win 7

saludos
DM

I recommend to install the new backports for a better performance with the wifi:
```

sudo apt-get install linux-backports-modules-karmic-generic
sudo apt-get install linux-backports-modules-wireless-karmic-generic
```

I still can't fix the "ctrl" key issue and the brightness stuff...

---

### Post by guv999 on 2010-03-19
> **donmatas said:**
> I recommend to install the new backports for a better performance with the wifi:
```

sudo apt-get install linux-backports-modules-karmic-generic
sudo apt-get install linux-backports-modules-wireless-karmic-generic
```

I still can't fix the "ctrl" key issue and the brightness stuff...


Ho Donmatas - just want to clarify something with you - if I install the backports as you describe will WIFI work with a normal Karmic install?   Would I not have to install any drivers etc  Thanks for your help

---

### Post by donmatas on 2010-03-19
> **guv999 said:**
> Ho Donmatas - just want to clarify something with you - if I install the backports as you describe will WIFI work with a normal Karmic install?   Would I not have to install any drivers etc  Thanks for your help

yes Guv, it will work's just installing karmic and the backports. No special driver needed. 
For been sure if karmic works on your computer, run in live mode and install the backports as i told you

salud
DM

---

### Post by satnelav on 2010-03-21
Hi,

I have exactly the same problem and the same configuration (Samsung N210, Realtek Semiconductor Co., Ltd. Device [10ec:8192] (rev 01)) as the third poster, suffice. Two of the mentioned solutions do not quite work for me on the current (21 Mar 2009) version of UNR. Downloading the backports as suggested by donmatas didn't make wireless available and compiling the driver from rapidshare as suggested by chili555 made wireless work, but broke standby and hibernate.

So I think we still don't have a good solution?

---

### Post by drspikes on 2010-04-04
I've got 9.10 NRU running on Samsung n210 with same wifi card as previous posts.

I carried out Chilli's method and did get Wifi but confirm it broke Standby and Hibernate.   However, Ctrl-C/V etc work fine for me.

I am quite new to this so would appreciate knowing what other people think.   1) Is this something someone should report a bug for in terms of breaking Standby?  Or is it our fault for installing a non-supported driver?

I was thinking of doing modprobe -r r8192e-pci to remove the driver and try the backports or failing this, NDIS method.

2) Has anyone removed this driver this way and restored standby?  
Is there a better method of removing?

Many thanks,

---

### Post by drspikes on 2010-04-04
> **drspikes said:**
> 
I was thinking of doing modprobe -r r8192e-pci to remove the driver and try the backports or failing this, NDIS method.


I carried out this instruction both as sudo su and normal user and got no error message.  ?Unfortunately, I've still got wifi access and it still hangs on Suspend or Hibernate.

Can anyone help me in getting back to how my system was so I can do the backport method?

Edit > OK got out of that mess ... System > Administration > Hardware Drivers. I could disable the driver and got back Suspend and Hibernation.

I'll try the backports when I get wired access tomorrow.

---

### Post by drspikes on 2010-04-05
> **donmatas said:**
> yes Guv, it will work's just installing karmic and the backports. No special driver needed. 
For been sure if karmic works on your computer, run in live mode and install the backports as i told you

salud
DM

OK I ran those two lines to install the backports and got messages saying it had done this fine but on reboot still no wifi.  ?Feels like I still need to install drivers.  Repeating the apt-get commands confirm the drivers are up-to-date.  Don't know what I'm doing wrong.


I've had a go at making use of NDISWRAPPER.  Basically I have failed to find/extract the XP drivers.   So far I downloaded the zip file from the samsung website, unzipped it then tried to use cabextract on Data1.cab and Data2.cab but am told they don't contain anything.  Please help - I'm stuck needing the relavent driver files.

Many thanks

---

### Post by donmatas on 2010-04-05
> **drspikes said:**
> OK I ran those two lines to install the backports and got messages saying it had done this fine but on reboot still no wifi.  ?Feels like I still need to install drivers.  Repeating the apt-get commands confirm the drivers are up-to-date.  Don't know what I'm doing wrong.

Many thanks

it's weird. My wife is using she's Samsung n210 without any problem...

salud
DM

---

### Post by drspikes on 2010-04-08
Hi everyone,

Forget backports etc.

The latest driver from Realtek works perfectly.  The only downside is that it needs reinstalling when the kernel get updated.

The driver file is:
rtl8192e_linux_2.6.0013.0127.2010.tar.gz

Instructions are:

1. Change to the driver directory
2. sudo su
3. make
(*if you are reinstalling 3b. make clean)
4. make install
5.reboot
6. ./wlan0up or ./wlan1up
     Note: 1. if permission denied, change perperty with `chmod 777 wlan0up`
           2. or enable driver with `ifconfig wlanx up`(wlanx denote wlan interface name).

The driver will be emailed to you if you request it from [email]wlanfae@realtek.com[/email].   They emailed back within 5 minutes!

I'm sure it is findable on the internet otherwise but surely best get get it un-tainted from source?

Best of luck.

---

### Post by olig1905 on 2010-06-02
> **drspikes said:**
> Hi everyone,

Forget backports etc.

The latest driver from Realtek works perfectly.  The only downside is that it needs reinstalling when the kernel get updated.

The driver file is:
rtl8192e_linux_2.6.0013.0127.2010.tar.gz

Instructions are:

1. Change to the driver directory
2. sudo su
3. make
(*if you are reinstalling 3b. make clean)
4. make install
5.reboot
6. ./wlan0up or ./wlan1up
     Note: 1. if permission denied, change perperty with `chmod 777 wlan0up`
           2. or enable driver with `ifconfig wlanx up`(wlanx denote wlan interface name).

The driver will be emailed to you if you request it from [EMAIL="wlanfae@realtek.com"]wlanfae@realtek.com[/EMAIL].   They emailed back within 5 minutes!

I'm sure it is findable on the internet otherwise but surely best get get it un-tainted from source?

Best of luck.

How do i do this i have the driver they emailed along with th instructions.. but these instructions are rubish, you cant just type make or make install. I am going to be honest i am kinda new to this how do i do it.

Also anyone with brightnes problem you can set the brightness to what you want before ubuntu boots and then it stays like that

---

### Post by drspikes on 2010-06-02
> **olig1905 said:**
> How do i do this i have the driver they emailed along with th instructions.. but these instructions are rubish, you cant just type make or make install. I am going to be honest i am kinda new to this how do i do it.

Also anyone with brightnes problem you can set the brightness to what you want before ubuntu boots and then it stays like that

Hi,  I'm no linux expert but I don't understand why you say these instructions are rubbish.

I will elaborate a little and then you need to specify why you feel what I've said is rubbish so I can help you most.

All the commands I have described need to be done in a terminal window.    

You need to know a couple of commands to get to wherever you have saved the driver files.   Best to google for instructions.  To change directory it is similar to old DOS except cd .. with a space to go up a directory level and cd \ rather than cd / for all directories you need to enter.  You can get it to complete any directory name if unique by starting the word and then pressing the tab key.   

When you are in the directory type the commands exactly as I have stated them.   If you get an error message it is very likely that you need to install "Build essentials" again do a google search to find out how to do these.

I want to help you but please be more specific.

Best wishes

Chris

---

### Post by drspikes on 2010-06-02
P.S. I knew I could adjust the brightness from the GRUB2 menu but I fail to see why this works in booting but not in Ubuntu - I don't want to have to restart if I forget to adjust brightness.

Ubuntu dims the screen when inactive for a while and then brightens again when I start working again so Ubuntu has some control over my computer brightness but there is nothing in settings I can manually adjust.

---

### Post by olig1905 on 2010-06-02
Yeh i knew all that!

i have come to the conclusion that they are not rubish i just have deeper problems ahaha i have started a new thread to resolve my problems

[http://ubuntuforums.org/showthread.php?t=1499820](http://ubuntuforums.org/showthread.php?t=1499820)

if you are intersted in helping

---

### Post by olig1905 on 2010-06-02
also i would love to get the brightness working aswell but as you can imagine the wireless is more of an issue for me..

---

### Post by northd_tech on 2010-06-06
> **drspikes said:**
> 
The driver file is:
rtl8192e_linux_2.6.0013.0127.2010.tar.gz

Instructions are:

1. Change to the driver directory
2. sudo su
3. make
(*if you are reinstalling 3b. make clean)
4. make install
5.reboot
6. ./wlan0up or ./wlan1up
     Note: 1. if permission denied, change perperty with `chmod 777 wlan0up`
           2. or enable driver with `ifconfig wlanx up`(wlanx denote wlan interface name).

Hi drspikes,

There is one problem if someone is reinstalling/recompiling the driver- #3a & 3b should be
```
make clean
make
```instead of "3. make" above, then continue at step 4 above.

Actually, it might be a good idea to run these 2 commands before running your set of instructions (Step -1 and Step 0 if you will ;)  ):

```
sudo depmod -a
sudo make modules_install
```

Hopefully, that will update and "synch" the other Linux modules before building the Realtek 8192E WiFi driver, in case there are any conflicts or missing dependencies.

I haven't tried this driver version personally yet- that Linux laptop's owner isn't around right now.  FWIW- there is a newer driver version "**rtl8192e_linux_2.6.0014.0401.2010.tar.gz**" listed on this thread:

[http://ubuntuforums.org/showthread.php?t=1460038](http://ubuntuforums.org/showthread.php?t=1460038)

That thread also mentions needing to copy the wireless firmware from one directory to another (and I remember doing this in my much earlier Realtek WiFi attempts and permissions were a problem copying them, but that was a long time ago).

It might be worth emailing Kidman/Realtek again and seeing if they have an even newer version that will work better (and be sure to specify whether you need 32- or 64-bit driver when emailing them).

I'll probably be trying this soon on that Toshiba Satellite P505D with Realtek 8192E WiFi (I think that the laptop owner installed a newer 64-bit unbuntu since I last tried it).  He has just been using the cabled ethernet connection since he bought the laptop months ago.

I'll try to save my steps and result output if I manage to finally get it working.

---

### Post by northd_tech on 2010-06-25
It sounds like someone(s) had success with 64-bit WiFi for the 8192E on this thread:

[http://ubuntuforums.org/showthread.php?t=1502752&page=2](http://ubuntuforums.org/showthread.php?t=1502752&page=2)

I can't **personally confirm** this, but I should have a Yes/No by next week if all goes as planned...

---

### Post by northd_tech on 2011-05-04
> **northd_tech said:**
> 
I'll try to save my steps and result output if I manage to finally get it working.

This is my most recent update for Realtek 81**92E** wireless:

[http://ubuntuforums.org/showthread.php?t=1689148&page=5](http://ubuntuforums.org/showthread.php?t=1689148&page=5)

---


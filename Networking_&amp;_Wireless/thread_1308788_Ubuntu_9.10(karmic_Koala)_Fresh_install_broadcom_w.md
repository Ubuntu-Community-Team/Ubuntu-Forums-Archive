---
title: "Ubuntu 9.10(karmic Koala) Fresh install broadcom wireless problems"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by r4z0rw0lf on 2009-10-31
so, i did a fresh install of ubuntu Karmic Koala
then tried to install my Broadcom wireless' firmware with
```

sudo apt-get install b43-fwcutter

```
i then restarted, it shows my driver is there in the Hardware Drivers window, but the wireless doesnt work

i then tried to deactivate it, and activated it, then it worked for about 10-30 seconds then stoped
dmesg | tail gave this
```

[  482.032599] b43legacy-phy1 debug: DMA-30 0x0260 (RX) max used slots: 1/64
[  482.032651] b43legacy-phy1 debug: DMA-30 0x0200 (RX) max used slots: 1/64
[  482.032705] b43legacy-phy1 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[  482.040061] b43legacy-phy1 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[  482.048054] b43legacy-phy1 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[  482.056055] b43legacy-phy1 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[  482.064226] b43legacy-phy1 debug: DMA-30 0x0220 (TX) max used slots: 20/128
[  482.072054] b43legacy-phy1 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[  482.080073] b43legacy-phy1 debug: Radio initialized
[  482.080091] b43legacy-phy1 debug: Radio initialized

```

---

### Post by r4z0rw0lf on 2009-10-31
bump

---

### Post by pdc on 2009-11-01
so you had a working version of Ubuntu before you did a fresh install of new software?

What didn't work on the previous (older) version?

---

### Post by r4z0rw0lf on 2009-11-01
the wireless was broken by trying to upgrade to karmic from jaunty, si i tried to fresh install, in hopes of fixing it

---

### Post by nuthead on 2009-11-03
I am running on a Dell Inspiron 1525 and upgraded from 9.04 to 9.10 and wirlesss kept on working. After a fresh install on the same machine the wireless did not work even after loading dksm and the Broadcom STA drivers separately. The drivers show in the Hardware Driver list but will not activate. In the upgraded system the STA drivers are listed and activated. So I know it will work but don't know how to activate it.

---

### Post by Daimoneze on 2009-11-03
I am having the same issue. It lists the device in the Restricted Drivers app, but will not activate it. This is a fresh install of Karmic. This computer is not within reach of the router so using the wired NIC is not possible. Is there way to manually install/activate the restricted Broadcom driver?

---

### Post by cerubim on 2009-11-03
Hi!

I'm having the same problem here. I have a Broadcom wireless card on my laptop and it wont recognize it. More so, I tried plugging in the wired connection and no transfer is going on.

Thanks.

---

### Post by gnuyoga on 2009-11-04
+1

---

### Post by CoyoteDen on 2009-11-04
Same problem here.

Dell Inspiron 14, BCM4322 a/b/g/n wireless, 9.10 karmic x64

Wireless network is WPA/WPA2 TKIP/AES on 2.4 and 5.2 GHz (different SSIDs)

 - STA driver shows up when I boot from the CD (USB stick, actually), will activate and I can see my WLAN, but it can't associate. I just get reprompted for the WPA passphrase every couple of minutes.

 - Once installed to the hard disk, nothing shows up under restricted drivers. If I manually reinstall the .debs (patch, dkms, bcmwl-kernel-soruce) i can get the STA driver to activate, but no dice on actually associating to my WLAN..

 - Under 9.04 everything just worked once the STA driver was activated, with the exception of never seeing the wireless-A (5GHz) network... maybe 802.11a/n just isn't supported by the STA driver.

---

### Post by rob.gilbert on 2009-11-04
I noticed a couple of things after fresh install of 9.10. WiFi didn't work. Based on broadcom chips.

One issue appeared to be under menu for user rights, network wireless did not have checkbox flagged to on.

Second: My wireless notebook has a Wifi switch on front edge that never worked under previous Ubuntu versions and now does.

---

### Post by Haythayt on 2009-11-04
I have the same problem with my Inspiron 1525.

However you can install the Broadcom driver yourself.

First download the archive with drivers here:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Then follow the official instructions:

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

In the end (after unloading other drivers possibly loaded and building the file => see instructions) you can activate you wifi-adapter with

sudo modprobe lib802011

and 

sudo insmod /path_to_extracted_build_file/wl.ko

As of yet I was not able to make this permanent. Both modules (lib80211 and wl.ko are not loaded during boot-up). So I have to load them manually when I restart my computer. But at least I have wlan-access.

Does anybody know how to add the modules permanently? Putting them in /lib/modules/... and adding them to /etc/modules did not do the trick...

---

### Post by coltranem on 2009-11-04
I had a similar problem when I upgraded to Karmic.  Instead of using the STA driver I created one using my old driver files from windows and ndiswrapper.  This seemed to work.  However I still had a problem when I were it would connect to the wireless network and then disconnect.  I was using WEP as security for my wireless.  When I switch to no security protocol everything works fine.  I would like to test out WPA but I haven't had time.

---

### Post by cruss575 on 2009-11-09
ok, i have some significant problems with this version.  I had a perfectly working version in jaunty, but went ahead and clicked the upgrade.   Anyway, I had the same problem with my wireless after I upgraded (no light, etc).  I tried to do the Active driver option in the Hardware Drivers applet, but it would not activate.  The jockey.log showed that the bcm43xx driver was being blacklisted.
The blacklist is maintained in the /etc/modprobe.d directory.  I changed the blacklist-bcm43.conf file to rem out the drivers being blacklisted and rebooted.  

The bcm43 driver never activated for me, but the b43 (fwcutter) driver did activate and it seems to be working correctly.

Now, back to my vmware compilation problem!

---

### Post by jeffmr on 2009-11-11
I've been playing around with this.  I haven't tested it fully but it seems to be working for a few minutes

look at what devices you have in ifconfig and deactivate all except lo and your wireless card.  Then disconnect from the network and reconnect.  

I'm using the sta drivers.  9.10 64 mbp 5,1

I had a virbr0 and my ethernet hardware that I disabled

sudo ifconfig yourdevice down

or up to bring back up

also, don't mess with any commands in terminal or network apps after that relating to network.

---

### Post by jeffmr on 2009-11-11
Still having the problem but if I close evolution, empathy and disable bluetooth, seems ok for now.

---

### Post by jagibbs on 2009-11-17
Same problem here...

[RANT] This is a fundamental problem with Linux.  Why is it that I always have to resort to "that other OS" for a working/reliable system and to get online to figure out what "secret/obvious" command I need to get my Linux system working again?  I understand Linux is more progressive an caters to a much wider audience then MS does, but that doesn't mean all of it's users WANT to have to spend hours searching for bug fixes and workarounds...  [/RANT]

[BODY]
I just upgraded to Xubuntu 9.10 from the previous version figuring everything would be OK, since in my past experience, it has been.  Little to my surprise, the mousepad on my Dell XPS M1330 has stopped functioning, my Broadcom wireless card has stopped functioning, and 50% of the times I reboot the system (normal or last known good configuration) it hangs and stops after doing a fsck.  I don't have access to a wired connection easily and I can't seem to install the Broadcom drivers from the 9.10 install iso CD I downloaded and burned.  From experience I KNOW there's an easy solution to fix this "bug" but I'm just too tired for the moment to look for the solution tonight..[/BODY]   OK, I guess that was actually a partial rant also.  Hopefully I can conjure up a couple hours tomorrow during my lunch break to figure out a solution.

---

### Post by tons-of-funs on 2009-11-17
when i had problems with my broadcom drivers what i did was hooked my computer up to an ethernet cord, searched for drivers(u may have to press check) and it found my driver installed it and i found my connections just fine

---

### Post by jthomsonmain on 2009-11-17
> **jagibbs said:**
> Same problem here...

[RANT] This is a fundamental problem with Linux.  Why is it that I always have to resort to "that other OS" for a working/reliable system and to get online to figure out what "secret/obvious" command I need to get my Linux system working again?  I understand Linux is more progressive an caters to a much wider audience then MS does, but that doesn't mean all of it's users WANT to have to spend hours searching for bug fixes and workarounds...  [/RANT]
I hate to be that guy that starts an argument, but the reason that Linux is so "hard" to use is the reason it appeals to such a wide range of people. When you have a system that is so open and modifiable as Linux is, it is going to be somewhat cryptic at times. If Linux was easy to use like Windows is, we would all be stuck using proprietary junk and Closed Source software, lol.

On a legitimate note, I am having the same problems on my netbook. I have an HP MiniNote 1000 and the broadcom wifi drivers aren't working. I will make a post if I find anything promising.

---

### Post by jthomsonmain on 2009-11-18
I ended up installing the bcmwl-kernel-source package and restarting and it magically worked, lol. Give it a try!

---

### Post by Neo40 on 2009-11-18
Yeah, another guy complaining about my wireless. I have a HP Pavilion dv2000 laptop and my wireless was working fine with previous version (9.04). Now its dead! 
Is there a fix somewhere??

Thanks

---

### Post by RwandaTim on 2009-11-20
Try the fix listed within the following thread (the first entry by Jomtois):  [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865).  Worked for me.

---

### Post by jintocd on 2009-11-20
Hi All,

I just solved the problem with my Lenovo G450 laptop with Boradcom wireless card. I already spend around one week fighting on this issue. Just now I resolved it! 

I just did what ever is given at 

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)


There is a readme.txt file. You please please follow this.

My network card details,

04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
07:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)

:popcorn:
Regards,
Jinto

---

### Post by dj63 on 2009-11-20
Hello

I also have the same problem on 9.10 with the broadcom wi-fi card, before i installed it (fresh install) i did (Live CD) Testing and it detected my wi-fi card (and all other restricted hardware) but after installing it as a second OS it wouldn't detect any of the restricted hardware.

---

### Post by netsecgeek on 2009-11-21
I have a Dell Vostro 200 Desktop with a Broadcom PCI card that identifies as the 4318 chipset.  On fresh install, the card is detected, but disabled.  Tried to activate driver in Hardware Drivers, but it would not activate.  Checked 'dmesg' and the error message sent me here: [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43).  Version 012 of b43-cutter was already on the system, so I performed these steps:

```

export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o
```Then Reboot.

---

### Post by cxwhite on 2009-11-24
I spent more time than I will admit on trying to get the broadcom linux driver working on my Dell x300.  Karmic Koala is my first go at Ubuntu, but I knew the wifi was working before I blew away XP.

I found advice in a similar thread that worked without a hitch:
[B]
sudo apt-get install b43-fwcutter[/B]
  
As soon as this command finished downloading the files, it immediately prompted me for a firmware installation. 

I said "yes" and off it went on its merry way.

The app reinstalled files that I had deleted or stepped on over the several days I spent wrestling with broadcom's driver. When I rebooted, all the familiar wireless networks in the neighborhood popped on the screen and I was able to connect to mine using wpa2 encryption.

-Chris

---

### Post by joker77 on 2009-11-25
I read the notes of the above posters, and installed **b43-fwcutter**, following the prompts. Nothing happened. 
Searched for anything to do with "broadcom". Found and installed **bcmwl-kernel-source** which includes dkms, fakeroot and patch. (just copying what I saw while installing, don't know what they are). Still nothing. **Rebooted**. Now its working fine and picking up signals. 

Anybody have any comparisons between the open source and the broadcom hybrid driver with respect to speed, etc?

---

### Post by derfflinger on 2009-11-26
> **jintocd said:**
> Hi All,


I just did what ever is given at 

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Jinto
Hi ! 
This work fine form me  too  !!! 

> **jintocd said:**
> : Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
07:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)

 Regards,
Jinto

My pc is a Dell Vostro 1000 and wireless is:
05:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

---

### Post by tumelo dlodlo on 2009-11-30
If any one uses emachines here is how to fix the wireless activation problem:

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

If you have a fresh ubuntu install it is very easy.:popcorn:

---

### Post by carlosve.ucv on 2009-11-30
This worked fine on my Hp dv4-1433us for my Broadcom WLAN.
**[SIZE=4]sudo aptitude install bcmwl-kernel-source[/SIZE]**
After that just reboot the machine and works like a charm.
Be carefull to activate your wireless button. It happend that it recognized my wlan and even the password popup showed up, but it never worked, all this because the wireless button was switched off even tho in ubuntu appeared to be on.

Hope this helps.

---

### Post by chuckles on 2009-12-13
Ok so I have a Dell Inspiron 8600 with Internal Broadcom wireless card.  It also has the Broadcom wired (b44) ethernet connection.   

Wired ethernet works fine.  

Wireless does not.  I have attempted the following so far.

FW-Cutter (both by Hardware Driver setup and by using Apt-Get)  

Removed Network-Manager and installed Wicd (did not work)

Looked for STA Drivers at broadcom site (no dice,  I have BCM 4306 chipset with PCI ID of 4320.  (Revision 2)  According Linux Wireless site, I need the B43-legacy driver.  (this is what the FW-Cutter tool is supposed to do)

Have looked at teh wpa-supplicant setup.  (i have no wpa-supplicant.conf file)  But not sure about this since Network-Manager runs this.  But even with security turned off both on the laptop, and the router, it still will not connect.

have also tried the sudo apt-get install bcmwl-kernel-source package... (this blew up all my network connections both wired and wireless)  Had to immediately issue sudo apt-get remove bcmwl-kernel-source after restart to get my basic wired network running again.

Also,other computers in the network will connect to router with no issues.  Actually this computer worked fine with this router when Windows XP was on it.  Router is a Linksys WRV210 VPN/Firewall wireless router.

Here is snipped of syslog file:


2009-12-13 12:20:08	Shitbox	wpa_supplicant[793]	Trying to associate with 00:21:29:e4:60:e0 (SSID='cassie_home' freq=2437 MHz)
2009-12-13 12:20:08	Shitbox	wpa_supplicant[793]	Association request to the driver failed
2009-12-13 12:20:08	Shitbox	kernel	[ 5121.828302] wlan0: direct probe to AP 00:21:29:e4:60:e0 try 1
2009-12-13 12:20:08	Shitbox	kernel	[ 5122.028245] wlan0: direct probe to AP 00:21:29:e4:60:e0 try 2
2009-12-13 12:20:08	Shitbox	kernel	[ 5122.228074] wlan0: direct probe to AP 00:21:29:e4:60:e0 try 3
2009-12-13 12:20:08	Shitbox	wpa_supplicant[793]	CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
2009-12-13 12:20:08	Shitbox	kernel	[ 5122.432036] wlan0: direct probe to AP 00:21:29:e4:60:e0 timed out
2009-12-13 12:20:12	Shitbox	wpa_supplicant[793]	CTRL-EVENT-SCAN-RESULTS 
2009-12-13 12:20:12	Shitbox	wpa_supplicant[793]	Trying to associate with 00:21:29:e4:60:e0 (SSID='cassie_home' freq=2437 MHz)
2009-12-13 12:20:12	Shitbox	wpa_supplicant[793]	Association request to the driver failed
2009-12-13 12:20:12	Shitbox	kernel	[ 5125.908303] wlan0: direct probe to AP 00:21:29:e4:60:e0 try 1
2009-12-13 12:20:12	Shitbox	kernel	[ 5126.108260] wlan0: direct probe to AP 00:21:29:e4:60:e0 try 2
2009-12-13 12:20:12	Shitbox	kernel	[ 5126.308277] wlan0: direct probe to AP 00:21:29:e4:60:e0 try 3
2009-12-13 12:20:13	Shitbox	wpa_supplicant[793]	CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
2009-12-13 12:20:13	Shitbox	kernel	[ 5126.508175] wlan0: direct probe to AP 00:21:29:e4:60:e0 timed out
2009-12-13 12:20:17	Shitbox	wpa_supplicant[793]	Authentication with 00:00:00:00:00:00 timed out.
2009-12-13 12:20:18	Shitbox	wpa_supplicant[793]	CTRL-EVENT-SCAN-RESULTS 
2009-12-13 12:20:25	Shitbox	wpa_supplicant[793]	CTRL-EVENT-SCAN-RESULTS 
2009-12-13 12:20:25	Shitbox	wpa_supplicant[793]	Trying to associate with 00:21:29:e4:60:e0 (SSID='cassie_home' freq=2437 MHz)
2009-12-13 12:20:25	Shitbox	wpa_supplicant[793]	Association request to the driver failed
2009-12-13 12:20:25	Shitbox	kernel	[ 5138.800111] wlan0: direct probe to AP 00:21:29:e4:60:e0 try 1
2009-12-13 12:20:25	Shitbox	kernel	[ 5139.000403] wlan0: direct probe to AP 00:21:29:e4:60:e0 try 2
2009-12-13 12:20:25	Shitbox	kernel	[ 5139.200245] wlan0: direct probe to AP 00:21:29:e4:60:e0 try 3


Any idea's???


Thanks,

---

### Post by deathbyswiftwind on 2009-12-13
My wifes laptop has an annoying issue with her broadcom. When I first installed 9.10 on it and did the broadcom driver everything appeared to work but it didnt. The wireless light was on and everything. By using the function key and they key to enable/disable wireless it worked. Weird though because when everything is good the light is supposed to be blue and when its disabled supposed to be orange now its the other way around but who knows it works :P

---

### Post by Daimoneze on 2009-12-14
My issue was fairly simple. The jockey (Hardware Drivers) application, which enables and disables restricted drivers, needed a package called b43-fwcutter. The effect is that it would see my wireless device but couldn't enable it. My solution was to use another machine (since I couldn't connect this computer via the NIC) to download the package and put it on a flash drive. I then installed it here and it worked. 

The command in the terminal would have been, as root:
```
apt-get install b43-fwcutter
```
This will apply if your wireless device is a BCM43xx.

---

### Post by linux6994 on 2009-12-14
I have had the same issues when I did my last fresh install of Ubuntu Karmic then I installed Linux Mint8 just to see if wireless would fly, I had already formated my partition anyway. Mint did the trick with all of my wireless issues and it's Karmic based anyway. Just a thought.

---

### Post by gsoundsgood on 2009-12-14
> **jthomsonmain said:**
> I ended up installing the bcmwl-kernel-source package and restarting and it magically worked, lol. Give it a try!

brilliant. just did it on a fresh install and it just worked. nothing else needed. thanks!!!

---

### Post by sibbers on 2009-12-18
I just did a fresh install on my laptop - Inspiron 300m - which has the BCM4309 chipset and it didn´t work out of the box.  The restricted drivers manager ran the b43-fwcutter fine, and dmesg showed the firmware being loaded.  Attempting to scan for networks didn´t work, turns out the wireless card was disabled (don´t know how, but fn+f2 fixed that).  Running ¨sudo iwlist scan¨ then showed wireless networks, so that was the first obstacle cleared.  

I couldn´t connect to my WPA2 network though, so I checked with wpa_supplicant: ¨sudo wpa_supplicant -Dwext -iwlan1 -c /etc/wpa_supplicant/¨ which showed that the connection was failing. I googled the error message and found  [http://ubuntuforums.org/showthread.php?t=1028638&page=1](http://ubuntuforums.org/showthread.php?t=1028638&page=1), which had the same symptoms. ¨sudo apt-get install --reinstall wpa_supplicant¨ as suggested on page 2 and it started working!

I guess there is some configuration issue with wpa_supplicant when it is setup.  Perhaps it is because the card is inactive when it is first installed due to the lack of firmware?

Either way it works fine now, so I hope this helps someone else!

---

### Post by billfinch on 2009-12-18
This is for chuckles....

I had lots of grief with almost the same config on a Presario M2000. My Broadcom is rev 03 but Dapperme 17 used almost the same method with 02. No flavor of b43 and ssb works with these older BCM chips as far as I can see.

Here's my post on how to solve it. I never really tried that hard with Karmic, but the principles are the same

Finally....

I got it going and here's how. First I went back to 8.04 Hardy. 9.10 Karmic wouldn't play nice.

First, it is imperative to get the right Win Driver, as all have noted. This is not trivial, as it appears BCM made a config du jour for the PC manf. I found the right one for my rev 03 card on the Compaq support site, not the HP support site. sp29361 for M2000 Presario.

I expanded this thing on my PC and copied the bcmwl5.inf and bcmwl5a.inf plus bcmwl5.sys to the Ubuntu machine into my user folder.

Then the technique is fairly simple. Thanks to Dapperme17 for the basics..You have to make sure the b43 and ssb modules are removed. I removed ndiswrapper as it was being loaded by somebody and I wanted a clean slate.

sudo rmmod b43
sudo rmmod ssb
sudo rmmod ndiswrapper


Installed the ndis gtk from the repository. I wanted to see what drivers I really was loading. Navigated to /home/bill/driver folder and selected both 5 and 5a as I wasn't sure what the significance of the "5a" was. No complaints, so I checked with lshw after doing a network restart. Everything looked clean and I had ndiswrapper re-installed.

sudo /etc/init.d/networking restart
sudo lshw -C network

I saw the ndiswrapper+bcmwl5 as the driver used. No lights, so I tried the switch and damn if it didn't turn on and connect! As stated in other posts it is easy to lose track of where the hardware switches are set.

To make this permanent, I created a shell script to run at start up based on help from dmizer among others.

Here's the code. I called my script wireless.sh.

sudo gedit /etc/init.d/wireless.sh

then write the script....

#!/bin/bash

sudo rmmod b43
sudo rmmod ssb
sudo rmmod ndiswrapper
modprobe ndiswrapper

Thats it. Save it. Now you have to make the script executable and update yet another file, rc.d.

sudo chmod +x /etc/init.d/wireless.sh
sudo update /etc/rc.d/ wireless.sh start s 50 .

The dot is important. Terminal should tell you the rcS has been updated

Reboot and it should all work.

This only took 3 weeks and there are probably a zillion things that could go wrong between distros and hardware and all. One thing for sure. b43 and ssb DO NOT WORK with the 4306 rev 03.

Good luck....:)

---

### Post by billstei on 2010-01-08
I did a fresh install of Karmic on a Dell Inspiron 1525 laptop and then I installed bcmwl-kernel-source (didn't need b43-fwcutter), and after a reboot the wireless was up and running fine.

---

### Post by rahul23 on 2010-01-10
> **carlosve.ucv said:**
> This worked fine on my Hp dv4-1433us for my Broadcom WLAN.
**[SIZE=4]sudo aptitude install bcmwl-kernel-source[/SIZE]**
After that just reboot the machine and works like a charm.
Be carefull to activate your wireless button. It happend that it recognized my wlan and even the password popup showed up, but it never worked, all this because the wireless button was switched off even tho in ubuntu appeared to be on.

Hope this helps.

thanks that worked for me on comapq 6710b .

---

### Post by RJKinsman on 2010-01-10
> **jagibbs said:**
> 

[RANT] This is a fundamental problem with Linux. Why is it that I always have to resort to "that other OS" for a working/reliable system and to get online to figure out what "secret/obvious" command I need to get my Linux system working again? I understand Linux is more progressive an caters to a much wider audience then MS does, but that doesn't mean all of it's users WANT to have to spend hours searching for bug fixes and workarounds... [/RANT]


+1 to your rant!

---

### Post by aganhuyag on 2010-01-31
Wireless device was not recognized after fresh install on Acer Aspire 5102 and I installed the driver below.. and it worked!
```

apt-get install b43-fwcutter
```

---

### Post by streever on 2010-02-01
> **Haythayt said:**
> I have the same problem with my Inspiron 1525.

However you can install the Broadcom driver yourself.

First download the archive with drivers here:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Then follow the official instructions:

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

In the end (after unloading other drivers possibly loaded and building the file => see instructions) you can activate you wifi-adapter with

sudo modprobe lib802011

and 

sudo insmod /path_to_extracted_build_file/wl.ko

As of yet I was not able to make this permanent. Both modules (lib80211 and wl.ko are not loaded during boot-up). So I have to load them manually when I restart my computer. But at least I have wlan-access.

Does anybody know how to add the modules permanently? Putting them in /lib/modules/... and adding them to /etc/modules did not do the trick...

OK, so I am using a compaq v6120US, with broadcom.

I followed the official instructions at the Broadcom site, and I was online.

Then I rebooted, and I was off-line.

I tried the two commands above but they returned errors. I then tried the bw-43fcutter command and it installed. I rebooted, and no internet :D

Any help greatly appreciated!

---

### Post by neo1786 on 2010-02-23
Wifi didnt work on my hp dv41433us.. after reinstalling karmic....worked fine with jaunty..worked fine when upgraded to karmic koala the first time...updated to a new kernel...uninstalled..reinstalled ...blah blah...no wifi

sudo apt-get install b43-fwcutter
reboot

works fine now..thanks guys :D

---

### Post by Minipalmer on 2010-03-22
Sorry to gravedig,

But the command "sudo apt-get install b43-fwcutter" from OP worked on my Kubuntu 9.10 install on my Dell Inspiron 1525. 

Thanks! 8 hours of looking paid off.

---

### Post by FredMalone on 2010-03-22
I had the same problem with my Dell 1520 laptop.  I was using 9.04 just fine and upgraded to 9.10.  It worked for a while then just stopped working after I did an update along the way.  I could not figure it out.  I tried the STA drivers and b43fwcutter drivers.  I could not get anything to work.

I then did an update to 10.04 beta to see if that would work.  Nada.  I then did a clean install of 9.10 and it still didn't work.

I should say that the wireless was disabled and I couldn't get it enabled at all.  I never did try the source package mentioned above.  However, I did find a solution.

In the BIOS for my laptop I changed the Wireless Switch setting to None.  I don't have or use the other options so I didn't need them.  This fixed this issue while using the STA drivers.

I wonder why this happened, though.  I never touched the BIOS when it stopped working.  Hmmm.

---

### Post by ddr71m on 2011-02-27
> **nuthead said:**
> I am running on a Dell Inspiron 1525 and upgraded from 9.04 to 9.10 and wirlesss kept on working. After a fresh install on the same machine the wireless did not work even after loading dksm and the Broadcom STA drivers separately. The drivers show in the Hardware Driver list but will not activate. In the upgraded system the STA drivers are listed and activated. So I know it will work but don't know how to activate it.

hey...i am having the same problems as yours....did you get that fixed...plzz..help me out..

---

### Post by Daimoneze on 2011-02-27
Hello ddr71m. It looks like you've stumbled on an old thread. You might want to consider starting a new one. Also, if you're still using 9.10, you might want to consider upgrading to a new version.

---


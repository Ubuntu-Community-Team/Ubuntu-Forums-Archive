---
title: "internet connection problems after fresh install of Ubuntu 12.04 LTS"
date: 2013-06-14
forum: Networking &amp; Wireless
---

### Post by jakacitizenoftheearth on 2013-06-14
Hello:

Completely new to Linux, but I am trying my best.  I apologize if I add more information than is needed, as I am still figuring out how to troubleshoot.

Hardware:  
VGA ASUS HD 7770-2GD5  2Gb Ram
8Gbx2-GSkill F3-1866c10D-16Gb Ram
128 GB Samsung SSD
HDD 3Tb Toshiba DT01ACA300
CPU-AMD-8Core-FX-8320-3.5G-8M-R
Gigabyte GA-990FXA-UD3 AM3+ AMD 990FX SATA 6Gb/s USB 3.0 ATX AMD Motherboard
Asus PCE-N10 Wireless-N Network Adapter (150 Mbs Transmit/Recieve) PCI-E interface-WPS
ASUS Vs228-H-P 22-Inch Full-HD 2ms LED-Lit LCD Monitor

System:  Ubuntu 12.04 LTS on entire SSD.

This is my first build, and I first dual installed Windows 8 and then ubuntu 12.04.  Both worked fine, with no issues that I could find.  But I hated Windows, so I decided to use a Linux only distro.  I tried for many days to install Debian (over the other OS's and not next to them), but it was to complex, and I couldn't handle the amount of problems I was having.  So, I decided to do a fresh install of the entire SSD.  Ubuntu installed correctly (from bootable usb) but could not connect to the Internet to install the rest of the packages, drivers, firmware, etc.  My wireless N-adapter shows my networks, but when I give it the correct password for my network it connects for about 15 seconds and then kicks me off.  It also will not connect to an Ethernet cable.  I cannot use my usb ports, I cannot use my mouse.  I can navigate to a terminal with my wired keyboard, and navigate the folders/files.  I tried: sudo apt-get update and other update commands, but without Internet there is nothing I can do.    Help please.

---

### Post by SylvesterYoo on 2013-06-14
How about plug your wireless adapter out and plug it back again?

---

### Post by jakacitizenoftheearth on 2013-06-14
Thanks Sylvesteryoo.  I did try that, and it did not help.

---

### Post by steeldriver on 2013-06-14
Sometimes wireless can be tricky - there are a couple of sticky threads in the 'Networking and Wireless' subforum with troubleshooting hints

To start, please open a terminal (Ctrl-Alt-t) and post the results of this command which should identify exactly what chipset we are dealing with

```
lspci -nn | grep -e '\[0200\]' -e '\[0280\]'
```

You can get further device / driver info with

```
sudo lshw -C network
```

I *think* it's a Realtek-based device and may need some work to get working in 12.04 but let's see

---

### Post by jakacitizenoftheearth on 2013-06-14
07:00 network controller [0280]: realtek semiconductor Co,. Ltd. RTL818CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)

---

### Post by jakacitizenoftheearth on 2013-06-14
the second command gives:   a lot of info, but I can't copy paste it.  here is the serial 10:bf:48:4a:84:ab

---

### Post by bustamanteguevara on 2013-06-14
I believe you should concentrate on installing the Ethernet first, and then the wireless, once you can update the software through the Ethernet. 

Do you have any other information about the ethernet adapter?

---

### Post by jakacitizenoftheearth on 2013-06-14
I will check later, as well as typing all the info from the second command.   For now I am AFK.  The girlfriend is dragging me to dinner.  Suppose I have to eat at some point...

---

### Post by jakacitizenoftheearth on 2013-06-15
Sorry it took so long:  I had to type it all by hand and it is like 02:00 here.  I really appreciate the help.  
after: sudo lshw -c network       
I get the following:
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet phy
sical tp mii 10 bt-fd 100bt  100bt-fd 1000bt 1000bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=
2.3LK NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no
multicast=yes port=MII speed=10mbit/s
resources: irq:75 ioport:b000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003ff
*-network
description: wireless interface
product: RTL8188CE 802.11/g/n wifi Adapter
vendor: Realtek Semiconductor Co., Ltd.
Physical id: 0
bus info: pci@0000.07.00.0
logical name: wlan0
version: 01
serial: 10:bf:48:4a:84:ab
width: 64 bits
clock 33 MHz
cpabilities: pm msi pciexpress bus_master cap_list ethernet physical
wireless
configuration: broadcast=yes driver=rtl8192ce driverversion=IEEE 802.11bgn
resources: irq:19 ioport:a000(size=256) memory:fe500000-fe503fff

My router is an old linksys, and my provider is comcast.  I have the same problem with the direct wired ethernet, it only connects for a couple seconds and then disconnects.  I can access the ip and netmask info from my laptop.  Is there any other information I need to configure a wired or wireless conection?  I don't think that the wireless receiver is at fault, since it show all of the networks.  Also, I had found a similar post earlier, but i did not understand its relevance to my issue.  : [http://ubuntuforums.org/showthread.php?t=2121599](http://ubuntuforums.org/showthread.php?t=2121599)

---

### Post by Rebelli0us on 2013-06-15
That's very unusual, AM3+ platform is very well supported.  Install takes less than 15 mins, can you reinstall using a different installation medium?

---

### Post by jakacitizenoftheearth on 2013-06-15
I don't have an optical drive.  This image installed fine in my laptop.

---

### Post by jakacitizenoftheearth on 2013-06-15
I just can't understand why it connects for a few seconds and then disconnects.  It must have been some kind of firmware issue that is left over from my failed Debian install.  Can I force it to stay connected?, is there a way to wipe all of the network settings for the hardline, and the wireless, and try reformatting them?

---

### Post by steeldriver on 2013-06-15
The other thread you found is afaik an issue specific to Intel devices (iwlwifi driver)

It  looks like the driver is loading and (as you pointed out) the wireless  scan is finding networks - so the question is why it is not able to stay connected (or 'associated') with your particular access point - you may find some useful messages in the dmesg log e.g.

```
dmesg | grep wlan0
```

Your wired device appears to be another Realtek, it *may* be picking up the wrong driver (r8169 versus r8168)

---

### Post by jakacitizenoftheearth on 2013-06-15
[     2.741201] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[     2.742536] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[     5.317017] wlan0: authenticate with 00:26:f2:92:64:da
[     5.326687] wlan0: Wrong control chanel: center-freq: 2462 ht-cfreq: 0 ht->
primary_chan: 15 band: 0. Disabling HT.
[     5.336784] wlan0: direct probe to 00:26:f2:92:64:da (try1/3)
[     5.540324] wlan0: direct probe to 00:26:f2:92:64:da (try2/3)
[     5.744137] wlan0: direct probe to 00:26:f2:92:64:da (try3/3)
[     5.947915] wlan0: authentication with 00:26:f2:92:64:da timed out

---

### Post by jakacitizenoftheearth on 2013-06-15
Out of desperation I tried a reinstall from the same USB.  Same problems as before, no usb ports, attempts to connect to the internet every 10-15 seconds or so, both wired and wireless.  It was even doing so during install (at the connect to Internet to install 3rd party software stage.)   I am at a loss.  *also, I did discover that I can in-fact use my mouse if I plug it into one of the usb 3.0 prts in the back.  ***Then I tried a usb in the same port and it worked!!!!   So, In theory, I can download files onto my laptop, load them on the usb, and put them on the computer.  Don't know why that happened after re-install, but anything I can do with it?

---

### Post by jakacitizenoftheearth on 2013-06-15
Is there perhaps some sort of step-by step Internet terminal set up that I can do?

---

### Post by wildmanne39 on 2013-06-15
*Thread moved to **Networking & Wireless**.*

---

### Post by wildmanne39 on 2013-06-16
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by jakacitizenoftheearth on 2013-06-16
I downloaded the script to a usb.  When I try to turn it into an exe file via: properties> make executable , it does not allow me to change it.  I can open the file in gedit, but I can't save it as exe.


*Sorry.  I still had it on the USB.  I put it on the desktop and was able to do so.

---

### Post by jakacitizenoftheearth on 2013-06-16
delete me

---

### Post by jakacitizenoftheearth on 2013-06-16
[ATTACH]243883[/ATTACH]

---

### Post by wildmanne39 on 2013-06-16
Hi, have you went to the top right of your secreen and made sure that wireless is enabled?

Please do everything in post 6 of the link below.
[http://ubuntuforums.org/showthread.php?p=12171877#post12171877](http://ubuntuforums.org/showthread.php?p=12171877#post12171877)

---

### Post by jakacitizenoftheearth on 2013-06-16
The wireless was disabled when I did the first wireless_script, since it kept prompting me every 10 seconds for a wireless key.  I did: gksudo gedit /etc/modprobe.d/rtl8192ce.conf   Then  I created:  options rtl8192ce swenc=1  Then rebooted.  Then I made sure my wireless was turned on and redid the Wireless_script.exe.  I attached the new results.   I also saw that in post 6 it said, "Also go into your router settings and change 802.11bgn to 802.11bg."  I did not know if this was relevant, nor how to do it, so I did not do it.  Should I have?  [ATTACH]243891[/ATTACH]

---

### Post by wildmanne39 on 2013-06-16
Hi, this driver is problematic in linux and requires some work.
> Also go into your router settings and change 802.11bgn to 802.11bg.it looks like you do not have that option but please check amd make sure.

Go into your router by entering 192.168.0.1 see if that gets you in.

Then look for a drop down menu and see if you can change it.
Also change your encryption in the router to wpa2 AES only if you have that option.

Then go into network manger top right corner and set security to wpa/wpa2.
Reboot
Thanks

---

### Post by jakacitizenoftheearth on 2013-06-16
I logged in to the router via my laptop, which was on the WiFi with 192.168.1.1.  I changed the security to wpa2.  Now I cannot get on the WiFi on my laptop either, and I have lost access to the router...

I reset the router and now I can access the wired connection on my laptop

I reset the router, and now all the other computers in the house can get on the wifi, and wired Internet.  same issue with my Ubuntu desktop.

*I also noticed that my mac adress is different on my laptop (which the wired Internet works on) and my pc. Don't know if that is supposed to happen

I still don't know what to do as far as solving this issue.  It really bugs me that I can't connect to the internet via a wired connection.   I have started reading how to configure connections manually in the terminal, but it is a bit advanced, and I still don't know what the root problem is.  One thing is for certain, my Ubuntu desktop is dead-in-the-water until I can get some form of internet connection.  I imagine most of the other errors can be fixed with updates and drivers.  Any additional advise is much appreciated.

---

### Post by jakacitizenoftheearth on 2013-06-20
I also tried following the instructions here: [www.youtube.com/watch?v=QFh2EZhUKgs]("http://www.youtube.com/watch?v=QFh2EZhUKgs")  ...to no avail.   I think I will try yet another fresh install, this time with a new .iso, maybe 13.04.  Wish me luck!

After yet another fresh install, this time a brand new .iso of 13.04, I have concluded that the issue is almost certainly with the firmware/hardware for my wireless card or motherboard.  Reasoning: the internet works fine on all other computers, the wifi works fine on all other computers, reinstalling OS does nothing, reinstalling drivers for my wireless card does nothing, my wireless card can detect wireless networks, the wireless card has a good signal with the wireless router, a direct connection via the Ethernet cable does not work either.   I will start searching for posts on checking/updating firmware.

---

### Post by Rebelli0us on 2013-06-21
I agree, it sounds like a hardware problem, lan/wifi card defects are common.

---

### Post by wildmanne39 on 2013-06-21
Hi, sorry I have not been on much I am having health issues and I am taking more time to tryh to get well.

The wireless and wired issues are to separate issues.

For the wired connection please do what is in this link post 4.
[http://ubuntuforums.org/showthread.php?t=2155983](http://ubuntuforums.org/showthread.php?t=2155983)
Thanks

---

### Post by varunendra on 2013-06-22
jakacitizenoftheearth,

The driver for your wireless also has been problematic for some users. Try installing the proprietary one downloaded from Realtek's site. Follow this post : [http://ubuntuforums.org/showthread.php?t=2156007&p=12700188#post12700188](http://ubuntuforums.org/showthread.php?t=2156007&p=12700188#post12700188)

Replace the first command of the 4th step of that post with -
```
apt-get install --print-uris build-essential linux-headers-generic
```

This will give you, among a few other details, the download links of the packages instead of trying to download them. Copy these links and use them to download the packages on a different computer where internet is working. Copy the downloaded packages to the your Ubuntu machine, then -

[INDENT]**1)** Create a new folder, say, "jack" on your desktop.

**2)** Copy the downloaded files into this folder.

**3)** Open a terminal and do -
```
cd ~/Desktop/jack
sudo dpkg -i *
```
to install the packages.

**4)** After the packages have been installed successfully, proceed with the other steps in the above linked post.[/INDENT]

Post back if you have any confusion or if there are any errors during the whole process.

---

### Post by jakacitizenoftheearth on 2013-06-25
I am having an error during install.  I don't understand it all, but I am pasting it.  It is mentioning Debian, I had a Debian install attempt a while ago, but I installed over it like 3 times.

What I did:  1. Downloaded the RTl8188CE driver for kernel 2.6.24 on my laptop
2. loaded the file onto a USB and then moved it to the desktop of my PC  
3. extracted the files from the compressed package
4. changed directories to the folder on the desktop
5. ran Code: sudo dpkg -i *
6. got this list of errors and pasting them here:

jak@jak:~/Desktop/files$ sudo dpkg -i *
dpkg-split: error: error reading rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013: Is a directory
dpkg: error processing rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013
jak@jak:~/Desktop/files$ cd /home/jak/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013
jak@jak:~/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ sudo dpkg -i *
dpkg-deb: error: `base.c' is not a debian format archive
dpkg: error processing base.c (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `base.h' is not a debian format archive
dpkg: error processing base.h (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `cam.c' is not a debian format archive
dpkg: error processing cam.c (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `cam.h' is not a debian format archive
dpkg: error processing cam.h (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-split: error: error reading compat: Is a directory
dpkg: error processing compat (--install):
 subprocess dpkg-split returned error exit status 2
dpkg-deb: error: `compat.h' is not a debian format archive
dpkg: error processing compat.h (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `compat-wireless-3.0-2-mesh.tar.bz2' is not a debian format archive
dpkg: error processing compat-wireless-3.0-2-mesh.tar.bz2 (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `compat-wireless-3.0-2.tar.bz2' is not a debian format archive
dpkg: error processing compat-wireless-3.0-2.tar.bz2 (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `compat-wireless-3.2.5-1.tar.bz2' is not a debian format archive
dpkg: error processing compat-wireless-3.2.5-1.tar.bz2 (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `core.c' is not a debian format archive
dpkg: error processing core.c (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `core.h' is not a debian format archive
dpkg: error processing core.h (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `debug.c' is not a debian format archive
dpkg: error processing debug.c (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `debug.h' is not a debian format archive
dpkg: error processing debug.h (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `efuse.c' is not a debian format archive
dpkg: error processing efuse.c (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `efuse.h' is not a debian format archive
dpkg: error processing efuse.h (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-split: error: error reading firmware: Is a directory
dpkg: error processing firmware (--install):
 subprocess dpkg-split returned error exit status 2
dpkg-deb: error: `Kconfig' is not a debian format archive
dpkg: error processing Kconfig (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `Makefile' is not a debian format archive
dpkg: error processing Makefile (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `pci.c' is not a debian format archive
dpkg: error processing pci.c (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `pci.h' is not a debian format archive
dpkg: error processing pci.h (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `ps.c' is not a debian format archive
dpkg: error processing ps.c (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `ps.h' is not a debian format archive
dpkg: error processing ps.h (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `rc.c' is not a debian format archive
dpkg: error processing rc.c (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `rc.h' is not a debian format archive
dpkg: error processing rc.h (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `readme' is not a debian format archive
dpkg: error processing readme (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `regd.c' is not a debian format archive
dpkg: error processing regd.c (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `regd.h' is not a debian format archive
dpkg: error processing regd.h (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `release_note' is not a debian format archive
dpkg: error processing release_note (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-split: error: error reading rtl8188ee: Is a directory
dpkg: error processing rtl8188ee (--install):
 subprocess dpkg-split returned error exit status 2
dpkg-split: error: error reading rtl8192ce: Is a directory
dpkg: error processing rtl8192ce (--install):
 subprocess dpkg-split returned error exit status 2
dpkg-split: error: error reading rtl8192de: Is a directory
dpkg: error processing rtl8192de (--install):
 subprocess dpkg-split returned error exit status 2
dpkg-split: error: error reading rtl8192se: Is a directory
dpkg: error processing rtl8192se (--install):
 subprocess dpkg-split returned error exit status 2
dpkg-split: error: error reading rtl8723e: Is a directory
dpkg: error processing rtl8723e (--install):
 subprocess dpkg-split returned error exit status 2
dpkg-deb: error: `stats.c' is not a debian format archive
dpkg: error processing stats.c (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `stats.h' is not a debian format archive
dpkg: error processing stats.h (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `wifi.h' is not a debian format archive
dpkg: error processing wifi.h (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 base.c
 base.h
 cam.c
 cam.h
 compat
 compat.h
 compat-wireless-3.0-2-mesh.tar.bz2
 compat-wireless-3.0-2.tar.bz2
 compat-wireless-3.2.5-1.tar.bz2
 core.c
 core.h
 debug.c
 debug.h
 efuse.c
 efuse.h
 firmware
 Kconfig
 Makefile
 pci.c
 pci.h
 ps.c
 ps.h
 rc.c
 rc.h
 readme
 regd.c
 regd.h
 release_note
 rtl8188ee
 rtl8192ce
 rtl8192de
 rtl8192se
 rtl8723e
 stats.c
 stats.h
 wifi.h
jak@jak:~/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$

---

### Post by varunendra on 2013-06-25
> **jakacitizenoftheearth said:**
> 
What I did:  1. Downloaded the RTl8188CE driver for kernel 2.6.24 on my laptop
2. loaded the file onto a USB and then moved it to the desktop of my PC  
3. extracted the files from the compressed package
4. changed directories to the folder on the desktop
5. **ran Code: [COLOR="#FF0000"]sudo dpkg -i *[/COLOR]**
6. got this list of errors and pasting them here:

Ah, that **dpkg -i *** command was meant for only the **linux-headers-generic** and **build-essential** packages (and others downloaded as their dependencies). Those two packages (+ other dependency packages) had to be copied to another (new & empty) folder where all of the above steps had to be performed. All these steps are substitute to only the first command in step 4 of the linked post. All the other steps in that posts, and other commands in step 4 have to be same as mentioned there.

For the driver installation, you will have to perform same steps as in the linked post. Only difference is that you don't have a cable connection either, so skip step 1, then replace only the first command in step 4 with the instructions in my previous post here.

---

### Post by jakacitizenoftheearth on 2013-06-25
Unrelated update: I plugged in a usb wireless device, and It was having the same exact connect/disconnect issue as the hardline and the wireless card.

Ok.  I am sorry, for still not getting this, but I am confused.  The very first command Code: apt-get install --print-uris build-essential linux-headers-generic  did not show the files I needed, it simply said they could not be found.  I did some research and I downloaded: build-essential_11.5ubuntu2amd64.deb & linux-headers-generic_3.8.0.26.44_amd64.deb    I then put them in a new folder on my desktop and tried Code: sudo dpkg -i *    The files failed to install, citing a need for dependencies.  I downloaded: dpkg_1.16.1.2ubuntu7.1.tar.bz2  &  g++4.7-multilib_4.7.3-1ubuntu1_amd64.deb  Finally, I put all four packages into the desktop folder and again tried code: sudo dpkg -i * and It was telling me I was missing other dependencies!!!  

Perhaps I have to do a separate install step for these packages?

So I am quite confused.  I am posting a text of my last terminal command:

jak@jak:~$ cd /home/jak/Desktop/fold
jak@jak:~/Desktop/fold$ sudo dpkg -i *
[sudo] password for jak: 
(Reading database ... 155212 files and directories currently installed.)
Preparing to replace build-essential 11.5ubuntu2 (using build-essential_11.5ubuntu2_amd64.deb) ...
Unpacking replacement build-essential ...
dpkg-deb: error: `dpkg_1.16.1.2ubuntu7.1.tar.bz2' is not a debian format archive
dpkg: error processing dpkg_1.16.1.2ubuntu7.1.tar.bz2 (--install):
 subprocess dpkg-deb --control returned error exit status 2
Preparing to replace g++-4.7-multilib 4.7.3-1ubuntu1 (using g++-4.7-multilib_4.7.3-1ubuntu1_amd64.deb) ...
Unpacking replacement g++-4.7-multilib ...
Preparing to replace linux-headers-generic 3.8.0.26.44 (using linux-headers-generic_3.8.0.26.44_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on g++ (>= 4:4.4.3); however:
  Package g++ is not installed.
 build-essential depends on dpkg-dev (>= 1.13.5); however:
  Package dpkg-dev is not installed.

dpkg: error processing build-essential (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of g++-4.7-multilib:
 g++-4.7-multilib depends on g++-4.7 (= 4.7.3-1ubuntu1); however:
  Package g++-4.7 is not installed.
 g++-4.7-multilib depends on gcc-4.7-multilib (= 4.7.3-1ubuntu1); however:
  Package gcc-4.7-multilib is not installed.
 g++-4.7-multilib depends on lib32stdc++6-4.7-dev (= 4.7.3-1ubuntu1); however:
  Package lib32stdc++6-4.7-dev is not installed.
 g++-4.7-multilib depends on libx32stdc++6-4.7-dev (= 4.7.3-1ubuntu1); however:
  Package libx32stdc++6-4.7-dev is not installed.

dpkg: error processing g++-4.7-multilib (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.8.0-26-generic; however:
  Package linux-headers-3.8.0-26-generic is not installed.

dpkg: error processing linux-headers-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dpkg_1.16.1.2ubuntu7.1.tar.bz2
 build-essential
 g++-4.7-multilib
 linux-headers-generic

---

### Post by varunendra on 2013-06-26
> **jakacitizenoftheearth said:**
> The very first command Code: apt-get install --print-uris build-essential linux-headers-generic  did not show the files I needed, it simply said they could not be found.

Please post the output of that command instead.

Also these outputs -
```
dpkg --get-selections | egrep 'linux-headers|build-essential'
```

---

### Post by jakacitizenoftheearth on 2013-06-26
Having trouble with usb at the moment, so I am typing this out; I will look out for errors.

The results for the first command have changed, must be something I did after my install attempts.

using jak@jak:~$     I ran the following:

```
apt-get install --print-uris build-essential linux-headers-generic
```

Reading package lists... Done
Building dependency tree
reading state information... Done
build-essential is already the newest version.
linux-headers-generic is already the newest version.
You might want to run 'apt-get' -f install' to correct these:
The following packages have unmet dependencies:
  build-essential  :  Depends: g++ (>= 4:4.4.3) but it is not installable
                            Depends: dpkg-dev (>= 1.13.5) but it is not installable
 g++-4.7-multilib  :  Depends:  g++-4.7  (= 4.7.3-1ubuntu1) but is not installable 
                             Depends:  gcc-4.7-multilib (= 4.7.3-1ubuntu1) but is not installable
                             Depends:  lib32stdc++6-4.7-dev  (= 4.7.3-1ubuntu1) but is not installable
                             Depends:  libx32stdc++6-4.7-dev  (= 4.7.3-1ubuntu1) but is not installable
  linux-headers-generic  :  Depends:  linux-headers-3.8.0.26-generic but it is not installable
E:  Unmet dependencies.  Try  'apt-get -f install' with no packages (or specify a solution).


Then, I did:

```
dpkg --get-selections | egrep 'linux-headers|build-essential'
```

build-essential                                                                                           install
linux-headers-3.8.0-19                                                                     install
linux-headers-3.8.0-19-generic                                             install
linux-headers-generic                                                                       install
linux-headers-server                                                                          install


*This post keeps removing the extra spaces I typed in, but all of the text is there.

---

### Post by jakacitizenoftheearth on 2013-06-30
I decided to take drastic action and overwrite both my SSD and HDD with a slow write.  After doing this, I did yet another install of 13.04.  This time I have no bright graphical background.  I just have the black screen with login.  I think the fact that it installed this way, this time and not before, meant that there were old drivers from past installs on the system I was working with.  I will start a new thread, since this is a more basic offline install, and won't involve any software that was not included with 13.04.  Thank you all who helped me with this question!!!  I learned a lot, even if I couldn't get my desktop up and running.   I will have a new post up today, If you have any time to look at it.  Thanks again, really.

---


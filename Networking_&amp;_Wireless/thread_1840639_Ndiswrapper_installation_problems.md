---
title: "Ndiswrapper installation problems"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by contumacious on 2011-09-07
So I burned a copy of Ubuntu 11.04 the other day and was playing around with the live boot before installing. Launched Ndiswrapper from the software center and it installed fine. Today I do a full format and install Ubuntu onto my desktop, have a disk with the extracted wireless card drivers on it. First thing I do is load up the software center to install Ndiswrapper and now it wont install.
 
Any reason why when it was running off the live cd it worked and it is not?

---

### Post by wildmanne39 on 2011-09-07
Hi, I am not experienced with ndiswrapper but lets make sure you need it most people do not.

Please run these commands and post the results here:
```
cat /etc/lsb-release; uname -a
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
lsusb
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by mtrethowan on 2011-09-08
I have had the same problems with a Gateway using a Marvell MC85 that I am setting up for my nephew. I have done all of the info gathering using nm-tools, lspci -nn, iwconfig, commented out and uncommented blacklist items, used ndiswrapper, loaded and unloaded several drivers. I have tried several suggestions from several sites, some dating back to 2008 and nothing has worked. Some have claimed that they got theirs working but didn't have the consideration to post their solutions, so I believe these to be dubious. Natty runs great on my Acer. I may just reinstall Windows 7 on the Gateway once I get the new back-light driver board installed.:(

---

### Post by wildmanne39 on 2011-09-08
Hi mtrethowan, are you still wanting help? If so please stat a thread so we can keep things straight and I or someone else will help.
Thank you

---

### Post by contumacious on 2011-09-13
Please run these commands and post the results here:
```
cat /etc/lsb-release; uname -a
```
 
cat: /ect/lab-relase: No such file or directory
Linux Dell 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GUN/Linux
 
```
lspci -nn | grep -e 0280 -e 0200
```
 
00:19.0 Ethernet controller [0200]: Intel Corporation 82566DZC Gigabit Network Connection [8086:104b] (rev 02)
 
04:04.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce one 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02]
 
```
lsusb
```
 
Just comes up with keyboard and mouse.
 
```
lsmod
```
 
Comes up with too long a list to type since I've got to type this on another laptop since I don't have a way to hardwire my desktop.

---

### Post by praseodym on 2011-09-13
Hi,

for your wireless device you dont need ndiswrapper, so remove it completely:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
Download the attached firmware file, save it on your desktop and install it via:
```
sudo tar xvf ~/Desktop/Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

---


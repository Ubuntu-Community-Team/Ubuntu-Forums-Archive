---
title: "Broadcom BCM4311/Ubuntu 12.10/Dell Latitude D620"
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by chockopocko on 2013-01-30
Hi, I'm a Ubuntu newbie currently testing out Ubuntu 12.10 on a Live USB. From my network controller, there does not seem to be an option to connect to a wireless network. The wired connection via Ethernet cable worked fine.

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

I've tried the following to get my wireless to work:

[LIST]
[*]Turning on the bcmwl-kernel-source driver in "Additional Drivers": nothing happened.
[*]Typing in 
sudo apt-get --reinstall install bcmwl-kernel-source
[LIST]
[*]DKMS: install completed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb is in use by ssb_hcd
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
update-initramfs is disabled since running on read-only media
[/LIST]
 
[/LIST]
After getting the above, I tried:


sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
FATAL: Module ssb is in use.
this@this:~$ sudo modprobe wl
this@this:~$ 

-----------------------------------
I've also tried installing b43-fwcutter, but it isn't listed in Additional Drivers after my attempt. 

this@this:~$ sudo modprobe -r b43 ssb
FATAL: Module ssb is in use.
this@this:~$ sudo modprobe b43
this@this:~$ 

Any help would be much appreciated. Thanks. =)

---

### Post by chili555 on 2013-01-30
The Broadcom STA driver is incorrect for your device. Nice of Additional Drivers to offer you something that won't work, wasn't it? Hook up that ethernet for a few moments, open a terminal and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r wl && sudo modprobe b43
```Any improvement?

---

### Post by chockopocko on 2013-01-30
Thanks for the speedy reply!
Here's what I got from the terminal:

this@this:~$ sudo apt-get remove --purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
this@this:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-firmware-nonfree
this@this:~$ sudo modprobe -r wl && sudo modprobe b43
FATAL: Module wl not found.

I'm not sure what's going on.. I think it has something to do with my using Ubuntu on a Live USB?

---

### Post by chili555 on 2013-01-30
> I think it has something to do with my using Ubuntu on a Live USB?I'm not quite sure how that could be. Are you connected to the internet? linux-firmware-nonfree is an available package in 12.10. Please try this:```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
```Off for the evening; see you tomorrow.

---

### Post by chockopocko on 2013-01-31
Thanks so much for your help! I installed Ubuntu alongside WIndows 7, and followed your instructions. I had to restart my computer two times forcibly, but now under Additional Drivers, I have the linux-firmware-nonfree driver for a device known as "Unknown : Unknown." xP

But I can now connect to wifi networks! Thanks again, I'm loving Ubuntu! =D

---

### Post by chili555 on 2013-02-01
Glad it's working! As I implied above, don't fret about Additional Drivers too much. Your wireless is working and that's what we needed.

---


---
title: "Deleted wireless card firmware upon installing"
date: 2011-08-07
forum: Networking &amp; Wireless
---

### Post by sc8ing on 2011-08-07
I recently decided to make use of a computer that had been put away for a while by installing ubuntu on it. I went to do a full install of 11.04 (deleting all files and the other OS, windows) and everything went smooth until I realized that the wifi-card firmware had been deleted along with everything else. I can use an ethernet cable to connect to the internet, but no wi-fi. I tried googling to find the appropriate firmware, but none worked. I'm pretty sure it's a Broadcom chip, but I'm not completely sure. Thanks for any help :)

---

### Post by ~!geek!~ on 2011-08-07
Try to use "Additional drivers" application to look for the drivers ubuntu identifies on your machine. 
If this application is successful in searching the drivers for your hardware, install them one by one by clicking on "activate it" button. 
Broadcom driver for wifi is kinda' common one!!!

---

### Post by wildmanne39 on 2011-08-07
Hi, post the results of these commands here please:
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod | grep b43
```
Thank you

---

### Post by sc8ing on 2011-08-07
Here are the results of those commands:

**sudo lshw -C network**:


  *-network:0             
       description: Ethernet interface
       product: 21x4x DEC-Tulip compatible 10/100 Ethernet
       vendor: Davicom Semiconductor, Inc.
       physical id: b
       bus info: pci@0000:01:0b.0
       logical name: eth0
       version: 31
       serial: 00:80:ad:40:02:6c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=dmfe driverversion=1.36.4 latency=64 link=no maxlatency=40 mingnt=20 multicast=yes
       resources: irq:9 ioport:d800(size=256) memory:ff8fdc00-ff8fdcff memory:ff880000-ff8bffff
  *-network:1
       description: Ethernet interface
       product: 3c905 100BaseTX [Boomerang]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth1
       version: 00
       serial: 00:60:08:3f:e0:68
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10Mbit/s
       resources: irq:10 ioport:df00(size=64) memory:ff8e0000-ff8effff
  *-network:2 UNCLAIMED
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: d
       bus info: pci@0000:01:0d.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:ff8fe000-ff8fffff

**lspci -nn | grep 0280**

01:0d.0 Network controller [0280]: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller [14e4:4301] (rev 02)

**iwconfig**


lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

**rfkill list all**

(this didn't list anything at all, just printed out another command line)

**lsmod | grep b43**

(this didn't print anything either)

---

### Post by sc8ing on 2011-08-07
> **~!geek!~ said:**
> Try to use "Additional drivers" application to look for the drivers ubuntu identifies on your machine. 
If this application is successful in searching the drivers for your hardware, install them one by one by clicking on "activate it" button. 
Broadcom driver for wifi is kinda' common one!!!

Nothing came up... Does that mean that there isn't a wireless card in my system? :confused:

---

### Post by wildmanne39 on 2011-08-07
Hi, run this command in a terminal please:
```
sudo apt-get install firmware-b43legacy-installer && sudo apt-get install b43-fwcutter
```
Then disconnect your wired connection and restart your computer and your wireless should be working.

If not post back for my help, if it is please go to thread tools and mark the thread solved.
Thank you

---

### Post by sc8ing on 2011-08-07
I tried running that twice and rebooting to no avail. Here's the error it gave me:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43legacy-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:4301)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

An alert box also popped up, allowing me to report the error. It took me to this site: [https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/711397]("https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/711397")

Regards

---

### Post by wildmanne39 on 2011-08-07
Hi, open synaptic and type in bcm then remove any thing that is there with a green square next to it.

Then in synaptic click on settings, repositories, then put a check by multiverse.

Then run this command in a terminal:
```
sudo apt-get update && sudo apt-get upgrade
```
Then when the updates have finished installing run this again.
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43legacy-installer
``` 
Then unplug your wired connection and restart your computer.

---

### Post by sc8ing on 2011-08-07
Hey it worked! Thanks so much ! :)

---

### Post by wildmanne39 on 2011-08-07
Hi, your welcome! I am glad I could help.

---


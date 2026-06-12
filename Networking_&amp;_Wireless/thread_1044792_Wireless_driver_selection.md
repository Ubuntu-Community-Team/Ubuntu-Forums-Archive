---
title: "Wireless driver selection"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by bdub13 on 2009-01-19
I have a TER/GUSB-N Netopia USB Wireless Stick.  

buntu@ubuntu:~/Desktop/rt2570-cvs-2009011916/Module$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
_Bus 001 Device 004: ID 148f:9021 Ralink Technology, Corp. RT2501USB Wireless Adapter_
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I have tried the RT73 driver to no avail, and I also tried rt2570 (USB)

CVS hourly tarball: rt2570-CVS driver.  
 
I cannot not seem to get this wireless to work.  I have spent many hours working on this and I am getting nowhere fast.

Brian

---

### Post by kircher on 2009-06-14
I am in the same boat. I have the same chipset for my wireless adapter Searching the ubuntuforums site and elsewhere on the net has only led me to compiling the drivers myself from the source provided by Ralink. I'd be happy to attempt the compilation, but the release notes and readme are quite vague, and it's something I'm not willing to attempt without some solid background information. Has anyone any experience compiling the driver for this card?

---


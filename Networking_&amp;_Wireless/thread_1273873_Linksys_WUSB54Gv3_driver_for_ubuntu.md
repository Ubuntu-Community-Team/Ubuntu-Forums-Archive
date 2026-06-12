---
title: "Linksys WUSB54Gv3 driver for ubuntu"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by nusntu on 2009-09-23
Hi, sorry for opening up this new thread as i know there are lots of HOWTOs on installing this card on ubuntu. I have tried all the methods mentioned in thoese HOWTOs including ndiswrapper, rt73 driver, rt2870 driver from ralink website. None of them is working for me. I can build the module correctly and load it without any problems, the problem is the kernel module won't detect my wireless card. lsusb shows the id of the usb wireless card:
***Bus 001 Device 003: ID 1737:0077 Linksys***
 
This card is working under windows and i can see two files rt2870.inf and rt2870.sys under its installation directory "adapter\xp\x86\". Is there anyone encountered the same problem? Or can somebody give me any hints? I really appreciate it.

---


---
title: "BroadCom Wireless &amp; 9.10"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by spiritsongtress on 2009-12-05
I know I have a broad com card, but I can't get Ubuntu 9.10 to see the card ect. And I don't know what kind it is, I know back when I had 8.04 I had to sort of jerry-rig the drivers in some fashion.

I found the card: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)

But I'd like to know how to get it to work.

---

### Post by luomo on 2009-12-06
I have also same network card. Following are the two ways to solve the issue:
1. If you have Live CD of Ubuntu 9.10 then open it in your ubuntu 9.10 and /pool/main/b/b43-fwcutter/b43-fwcutter_012-1_i386.deb. Find this package and just double click it and it will be installed.
2)Go to this link:[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)and follow the instruction after:"You are using the b43 driver linux-2.6.25 or newer" and get it installed.

Reboot your system after installing the fwcutter.

---


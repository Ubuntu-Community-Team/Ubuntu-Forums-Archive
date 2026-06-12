---
title: "modeprobe wlunload removed my wifi drivers..."
date: 2011-10-31
forum: Networking &amp; Wireless
---

### Post by qbox on 2011-10-31
Hello..

At firs I use Ubuntu version 11.04
I have:

lspci

0c:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)

lsusb

Bus 002 Device 003: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n

both cards works GREAT before I make a mess..

I follow this tutorial 
[http://aircrack-ng.org/doku.php?id=compat-wireless](http://aircrack-ng.org/doku.php?id=compat-wireless)

and after command **sudo make wlunload** I lost both wifi devices. after that I sudo modprobe driver-name I get back usb device back on line and start working, but now I can't make my internal pci broadcom device to make it work....


any help please ? :(

---


---
title: "Broadcom BCM4306"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by triunenature on 2009-05-15
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

Thats the card, the computer is hp pavilion ze5700

Im using 8.04

Issue is simple, I cant get wireless network to work.  Its not even giving me wireless options.  I've read a million reports, but i dont know what to do exactly.  Any ideas?

---

### Post by triunenature on 2009-05-16
*bump*

---

### Post by triunenature on 2009-05-16
*bump*

---

### Post by spd106 on 2009-05-16
The easiest way is to connect up with an Ethernet cable temporarily and install the b43-fwcutter package via Synaptic. This will download the firmware and install it for you. You'll then just need to load the driver (or reboot) and it should start working.

Otherwise you'll have to find another way to download the firmware.
See [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)

---


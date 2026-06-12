---
title: "Marvell 88w8335 ndiswrapper driver installed + claimed, no wireless networks found."
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by Golevel on 2010-09-16
I'm using Wicd + ndiswrapper with my 88w8335 marvell libertas pci card.

Here's my details:

*-network:0             
       description: Ethernet interface
       product: 21x4x DEC-Tulip compatible 10/100 Ethernet
       vendor: Davicom Semiconductor, Inc.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 31
       serial: 00:08:a1:21:f6:85
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=dmfe driverversion=1.36.4 ip=192.168.1.137 latency=64 maxlatency=40 mingnt=20 multicast=yes
       resources: irq:16 ioport:ec00(size=256) memory:fe1ffc00-fe1ffcff memory:10000000-1003ffff(prefetchable)
  *-network:1
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: wlan0
       version: 03
       serial: 00:40:f4:e6:7b:7f
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+mrv8335 driverversion=1.55+Marvell,02/22/2005,3.1.1.7 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: irq:19 memory:fe1d0000-fe1dffff memory:fe1c0000-fe1cffff

It took me awhile to get to this point, but now that its claimed, it still doesn't pick up any wireless networks. I've got a computer next to me that can detect wireless networks in range (our router is 10 feet away). Any ideas?

---

### Post by Golevel on 2010-09-16
Solved this by uninstalling wicd and installing the generic "network manager"

---


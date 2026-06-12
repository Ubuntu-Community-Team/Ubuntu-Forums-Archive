---
title: "HP Mini 110 wireless Ubuntu 10.10"
date: 2011-04-21
forum: Networking &amp; Wireless
---

### Post by greatgoo on 2011-04-21
Wiped the 10.04 install and did a new 10.10 install and the wireless broke. I spent a day going through the posts trying to figure it out. Finally fixed it.

HP Mini 110  1030NR
PCI id 14e4:4315
Broadcom Corporation BCM4312 802.11b/g LP-PHY

I used Synaptic and searched for bcm.  Found several Broadcom packages, including an STA package which is recommended for this chipset.  I just installed them all and rebooted.  Worked fine.

David Davis
Newport, OR 97365

---


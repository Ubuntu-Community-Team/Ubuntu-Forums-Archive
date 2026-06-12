---
title: "Yet another BC43xx problem"
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by SenoraRaton on 2010-12-08
I have a broadcom 4312 chipset for my wireless card.  I have tried about 5 diffrent ways to install it, including using b43 cutter, using the "additional drivers" under system.  Nothing works... sort of.  I have had the driver download, and activate once, and then not work again.  Even when it said it was activated within Additional drivers, I still had no connection.  

I'm running Ubuntu 10.10 64 bit, it was a clean install before I started jumping through the hoops to get the wireless card to work.

lspci -
Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
Sometimes I recieve an error from jockey to check the log:

2010-12-08 11:43:29,425 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-12-08 11:43:34,723 DEBUG: Shutting down

Also now when I try to activate the driver in additional hardware, i receive an error installArchives() failed.

Nothing seems to work... properly

---


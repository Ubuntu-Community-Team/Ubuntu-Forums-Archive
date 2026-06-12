---
title: "Wireless Connection Speed"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by wah fun on 2010-02-03
After a good deal of work, I finally got the wireless network to connect using ndiswrapper. But, it only connects at 54Mbps whereas in windoze, the network connects at 135Mpbs - 150Mbps. Is this a limitation of ndiswrapper? I have googled the issue and the answer seems to be that ndiswrapper is limited to the 54Mbps max. If this is not true, can someone help me achieve the higher connect speed?

thx

Setup:
PC - 3 Gb ram, 2 GHz dual core processors
Belkin N150 Enhanced Wireless Router
Belkin N150 Enhanced Wireless USB Network Adapter
Ubuntu 9.04
Windows xp64 driver - rt2870.inf

I have tried compiling the ralink driver but have not been able to get it to work. I may not have the 64 bit driver from ralink (I am not sure if the one I dl'd is 64 bit or maybe one driver works on both - don't know).

Anyway, if someone has a good idea, I would appreciate hearing it.

thx

---

### Post by wah fun on 2010-02-08
OK. After hours of working, I have finally got the rt2870 native driver to compile and have blacklisted ndiswrapper. The new driver (v2.3.0.0) is working just fine EXCEPT that it too only connects at 54 Mpbs. Has anyone achieved the pre-N speeds (up to 150Mbps) with this device? In windoze, the typical connect speed is 135-150 mbps.

thx

---


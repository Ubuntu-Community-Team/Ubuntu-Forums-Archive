---
title: "D-Link DGE-528T - can't get gigabit speed to stick"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by |V|utley on 2010-09-29
Hi all,

I have a media server with Ubuntu 9.10 running on it.  I recently installed a new NIC, a D-Link DGE-528T, so that I could benefit from gbit speeds on my new gbit LAN.

The card installation was very straight forward, it uses the r8169 driver.  

However, the NIC always defaults to running at 100mb/s full duplex.  When I run ethtool, I see that 1000baseT/Full is supported but not listed under advertised link modes.

If I use this command:

ethtool -s eth1 advertise 0x020

After a short pause, all is good, and we're running at 1gbit.  However, this does not stick between suspend/resume or reboots. 

Any ideas on how to get this card to stick at 1gbit? 

TIA.

---


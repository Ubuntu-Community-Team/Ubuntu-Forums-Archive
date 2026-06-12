---
title: "no link after forcing to 10baseT-FD"
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by gareth00 on 2010-04-18
Hi all. I am trying to force my nic to 10Mbs using ethtool like so:
ethtool -s eth0 speed 10 duplex full autoneg off
 
However, each time I do so, the link goes down and is reflected as down in ethtool. This command works fine setting it to 100Mbs:
 
ethtool -s eth0 speed 100 duplex full autoneg off
 
It works fine when I set it to 10Mbs in Windows 7.
 
My nic is Marvell Yukon 88E8040. Tried on my installation of 8.04 and live CD 9.04 with the same results. 
 
Thanks!

---


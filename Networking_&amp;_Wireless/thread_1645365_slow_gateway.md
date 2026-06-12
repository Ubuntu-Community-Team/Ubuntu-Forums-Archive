---
title: "slow gateway"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by mimizone on 2010-12-14
Hi,

I have an old Ubuntu 6.x something box (running kernel 2.6.28) used as a NAT gateway between 2 networks.

the box has 2 NIC cards, one on each network.
10.33.x  (VLAN1, connected to the internet)
10.1.x (VLAN2, internal)

All the connections to the VLAN1 or outside world seems to be throttled to about 1.2Mbps. 
But I can't find anywhere where it could be configured as such.

ethtool and mii-tool confirm the NICs are configured at 1000Mbps.
The switches are not doing any traffic shaping and are not saturated. I've done some test of different cabling with other machines, and the issue definitely comes from the gateway.

It's only using some iptable rules.
It has well enough CPU and memory for the task.


Any clue?
Thanks for any pointers you can think about.

---


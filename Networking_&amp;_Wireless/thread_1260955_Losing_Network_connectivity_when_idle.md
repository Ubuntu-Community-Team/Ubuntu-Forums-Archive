---
title: "Losing Network connectivity when idle"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by PaulHeywood on 2009-09-08
Hi there, I have a problem where a linux server loses connection to a number of different types of equipment - this normally happens if the connection has been idle for a number of minutes. Traceroute and my understanding of how the network is physically setup imples that all of this is on the same network (no gateways involved).

As I know the MAC Addresses of the equipment I'm attempting to connect to I can set up a static ARP entries and everything is then ok (which seems to make sense as I probably lose connectivity after the cache has been cleared).

When the ARP cache is interrogated following a failure to ping a couple of devices then the MAC address for those failures is actually the same MAC address - I'm not sure if that is indicative of a problem or whether it's just the MAC address of the bit of equipment that I can reach (like a switch).

Last few things to mention is that there are other servers in the network that can still ping the problem IP Addresses when my server can't and finally if I power cycle the bit of equipment I'm trying to connect to then I connectivity is restored.

Any help would really be appreciated,

Paul.

---


---
title: "Cannot connect to external IPs"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by Megalomania on 2009-04-27
I recently installed Ubuntu 9.04 on a server and a VM (inside another server) and currently neither can ping external computers.  trying to do so brings up
"
connect: Network is unreachable
"

My network is configured to use my Server 2K8 AD DC/NPAS server as gateway, and both can ping anyone else on the network and can be accessed by anyone else on the network.  However, if I try to ping google, then the network is unreachable.  To just focus on one, its settings are address 192.168.1.3, netmask 255.255.255.0, gatewaqy 192.168.1.13, nameserver 192.168.1.13, 192.168.1.32.  192.168.1.13 and 192.168.1.32 are redundant nameservers in my domain.

I have four or five windows machines configured to use the same settings (with different IPs of course) and none of them has this issue.

---


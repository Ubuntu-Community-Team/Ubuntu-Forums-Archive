---
title: "Router prematurely wakes up DHCP server"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by jamesnewell on 2010-10-21
Hi all,

I've setup a gateway in my home office. To save the environment and money on electricity I've setup the gateway to power down and backup automatically. I've got the gateway powering back up via WOL when the network card receives a broadcast packet.

If the router has a static IP, the gateway stays off and later turns on as desired when a DHCP client starts.

However if the router is set to get an IP via DHCP the gateway automatically wakes up after ~10 seconds - even if the DHCP lease is infinite.

Why does the router send broadcast packets to find the DHCP server when it already has an infinite DHCP lease?

Thanks,

James

P.S. The router is an Apple Airport Extreme

---


---
title: "Dont allow traffic between virtual adapters"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by BlackCatSLO on 2008-12-29
Im having problems with virtual adapters on my "Router" machine.
Machine has 2 Ethernet cards one for inside other for outside traffic. The inside card has 2 virtual adapters like eth1:1 eth1:2. The inside network is split in two subnets the 10.5.5.0 and 10.10.10.0. 
The problem apears when i ping some machine on other subnet and that machine answers and when i try to do traceroute to other subnet the trafic goes:
10.5.5.234
10.5.5.1
10.10.10.34
Witch shows that the traffic goes over Router machine.

Is there any way to block all traffic between thows subnets traffic. For nat and firewalling im using iptables

---


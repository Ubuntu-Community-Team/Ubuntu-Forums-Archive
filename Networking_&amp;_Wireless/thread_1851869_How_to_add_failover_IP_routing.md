---
title: "How to add failover IP routing?"
date: 2011-09-29
forum: Networking &amp; Wireless
---

### Post by superman1 on 2011-09-29
Hi
 
I have two interfaces, eth0 and eth1 with ip 10.255.1.100 (GW  10.255.1.1) and 10.255.2.200 (GW: 10.255.2.1) subnet mask 255.255.255.0
I want to add failover routing to an IP 192.168.100.100 i.e 1st priority  route through GW 10.255.1.1 and second priority route through  10.255.2.1 (i.e primarily reach 192.168.100.100 through eth0 and try  through eth1 if eth0 is down or the ip cant be reached from eth0)
 
Is such a route definition possible in IP?
 
If yes, what would be the commands.
if not, why?
 
TIA,
 
Regards,
sm

---


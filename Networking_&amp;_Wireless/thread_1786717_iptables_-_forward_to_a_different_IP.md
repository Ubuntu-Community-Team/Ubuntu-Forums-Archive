---
title: "iptables - forward to a different IP"
date: 2011-06-20
forum: Networking &amp; Wireless
---

### Post by infant_coder on 2011-06-20
Hi,

I have three PC's connected to a router, PC1,PC2, PC3. I am trying to forward packets from PC2 to PC3 using the following command. But I ' m not able to do so. Please verify the command.


#On Router
Forwarding PC2 --> PC3

Command:

iptables -t nat -A PREROUTING -p tcp -d 192.168.11.50 -j DNAT --to-destination 192.168.11.40

---


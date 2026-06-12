---
title: "Advanced Routing using Firewall Mark"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by Craig1972 on 2011-02-04
Hi all:  

I would like to be able to policy route traffic based on marking packets.  In order to make this work it seems I need a couple of Kernel options:

IP: advanced router (CONFIG_IP_ADVANCED_ROUTER) [Y/n/?]
IP: policy routing (CONFIG_IP_MULTIPLE_TABLES) [Y/n/?]
IP: use netfilter MARK value as routing key (CONFIG_IP_ROUTE_FWMARK) [Y/n/?]

Can somebody tell me how to determine if the Kernel I am running has these options set?  Where do I look for this information?

I am running 9.10 - Kernel 2.6.31-22-generic-pae.  I know I have the first two options set, but not sure about the 3rd



Thanks

---


---
title: "Tricky problem with network interface card. Please help!!!"
date: 2013-06-21
forum: Networking &amp; Wireless
---

### Post by plopes on 2013-06-21
Hi.

I have two desktops (ubuntu 12.04 and lubuntu) directly connected to each other. Each machine haves 2 NICS (one is the PCI NIC). What im trying to do is directly connect each interface with static routes. If i connect both PCI interfaces with static routes the network works fine, but if i connect one PCI interface on machine A to the other NIC on machine B with static routes it doesn't work (strange isn't!). This happens in both ways and im testing with ping command. Even more weird happens when i connect the not PCI interfaces to another Windows laptop with static routes and it works.  
 
The lshw command shows that all 4 interfaces are activated. Routing tables are ok. The firewall (iptables) chains are all accept. 

I will preciate who answer me with a solution for my problem. Sorry for my bad english but it isnt my mother language.
 
Cya

---


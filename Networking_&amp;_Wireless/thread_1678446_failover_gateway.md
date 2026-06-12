---
title: "failover gateway"
date: 2011-01-30
forum: Networking &amp; Wireless
---

### Post by CaptainProton on 2011-01-30
hey there,

i have an ubuntu box using a default gateway (a NAT Rouer in my LAN) configured to eth0.
192.168.1.1

Now I've bought a 3G router that I want to use for failover. 

So my prefered solution would be simply connecting the 3g router to my LAN -eg. using 192.168.1.2 as IP of 3g router-  and adding a second interface eth0:1 with 192.168.1.2 as gateway to my /etc/network/interfaces.

That results in two default gateways on one machine. Without knowing alot of depth of linux routing, [B]I assume that only one gateway will be active.
But wich one?[/B] (in the regular case that both internet connections are available)

**And what will be if the gateway of eth0 is down? **Gateway of eth0:1 automatically being used?

For some particular reason I dont have the option to play arround with that server alot.  So I like to know beforehand whats gonna happen.

---


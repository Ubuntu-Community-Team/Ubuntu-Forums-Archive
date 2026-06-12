---
title: "Routing problem with two interfaces on the same network"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by needtosearchforum on 2009-05-27
I have two interfaces on my ubuntu 8.04 box which are both connected to my internal 1gbit switch here at home. My goal is to have 100Mbit/s download per interface. 

I added the following routes to make sure 10.0.0.121 uses eth0 and 10.0.0.132 uses eth1:

```
ip route add default via 10.0.0.1 dev eth0 tab 1
ip route add default via 10.0.0.1 dev eth2 tab 2

ip rule add from 10.0.0.121/32 tab 1 priority 500
ip rule add from 10.0.0.132/32 tab 2 priority 600

ip route flush cache
```

Which works great from my server (10.0.0.1) but no traffic from my lan (10.0.0.x) can reach 10.0.0.121 and 10.0.0.132. What did i miss in my rules and routes?

---

### Post by spd106 on 2009-05-27
I think you might have better results using interface bonding (link aggregation). I've never tried it myself, but it looks like fun.

See the following for more details:
[http://en.wikipedia.org/wiki/802.3ad](http://en.wikipedia.org/wiki/802.3ad)
[http://www.linuxhorizon.ro/bonding.html](http://www.linuxhorizon.ro/bonding.html)
[http://www.howtoforge.com/network_bonding_ubuntu_6.10](http://www.howtoforge.com/network_bonding_ubuntu_6.10)

---

### Post by Iowan on 2009-05-27
Routing problems would seem to be the normal result of having two interfaces in the same subnet... though I've seen some posts claiming it works (bridging???)

---

### Post by needtosearchforum on 2009-05-29
Interface bonding requires that the switch supports it unfortunately. 

I tried to just add the routing rule for the second interface (eth2) which seems to allow me to download 2x100Mbit from other boxes on my lan. I will test some more to see how well it works.

---

### Post by HDave on 2009-05-29
In your OP, you mentioned eth0 and eth1, but in the interfaces file you have eth0 and eth2.  Is this a type-o or the is this the problem?

---


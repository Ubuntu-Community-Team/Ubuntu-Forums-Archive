---
title: "Router with two internet connections"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by maximouse on 2009-10-01
I have a router with 2 dsl lines, one with 1 ip and the other with 16. I would like to set up the system so that all traffic goes through the 1 ip dsl line, except for incoming connections to one of the 16 ip:s.
I have looked at a lot of howto:s but most setup a much more complicated system.

The setup goes as follows:
eth0 84.x.x.82 (gateway 84.x.x.81)
eth0:0 84.x.x.83 
eth0:1 84.x.x.84
.....
eth1 192.168.1.1
eth2 213.x.x.154 (gateway 213.x.x.129)

---


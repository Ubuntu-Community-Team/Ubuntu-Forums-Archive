---
title: "help with dmz"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by ulao on 2010-09-01
I'm trying to use iptables so that all traffic in on eth0 goes to 192.168.0.25. Like a true DMZ.

the 192.168.x.x network is on a virtual nic eth0:1
eth0 is my out side nic.

Tried something like this no luck. 

iptables -t nat -A PREROUTING -p tcp -i eth0 -j DNAT --to-destination 192.168.0.25

--maybe I can do this but how can I do this with dhcp

iptables -t nat -A PREROUTING -d 97.158.253.26 -i eth0  -j DNAT --to-destination 192.168.0.25

---


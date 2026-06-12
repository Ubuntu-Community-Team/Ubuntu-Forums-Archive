---
title: "advanced routing: how to add routes for DHCP link?"
date: 2011-10-26
forum: Networking &amp; Wireless
---

### Post by beijingjj on 2011-10-26
I have setup a simple router using Ubuntu.  It has eth0, which is DHCP from my ISP, and ppp0, which is a pptp tunnel to New York.  (It also has eth1, which is local LAN traffic which I am routing out the two interfaces).  ppp0 is the default route.  Since I am in Asia, I have a series of routes to add to route my Asia-destined traffic out eth0 for better speed and latency.  

The problem is, since this is a DHCP connection, I don't know what the next hop IP address is in advance, so I can't automate the routing.

In my /etc/network/interfaces I have a series of lines like this:

up route add -net 1.0.0.0/8 gw a.b.c.d
up route add -net 14.0.0.0/8 gw a.b.c.d
up route add -net 27.0.0.0/8 gw a.b.c.d

How can I automate detection and insertion of a.b.c.d??

Thanks!

Beijingjj

---


---
title: "DSL/PPPoE with /30 subnet - how?"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by bjorn2die on 2009-06-19
I'm hoping to replace my ISP router with a linux box, the service is a DSL line with a PPPoE connection. I have a /30 subnet to play with.

eth0 is connected to the router, and after forcing the router to take down its PPPoE connection, I can use pon dsl-provider to bring ppp0 up. Lets call my linux host A with "public" ip n.n.n.77.

The question is, how do I get traffic from host B n.n.n.78/30 on eth1 through ppp0? ppp0 comes up as n.n.n.77/32 and I've tried enabling ip_forwarding and created a route to n.n.n.78 with /30 and /32 masks to eth1 with no sucess.

Is proxyarp the glue I'm missing? But pppd complains:
pppd[]: Cannot determine ethernet address for proxy ARP

I want to use the first public IP for NAT, and have the second public IP routed on eth1, but I could really use a kick in the right direction!

cheers,
Bjorn

---


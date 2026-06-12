---
title: "Ubuntu With Three NIC: 1xLAN, 2xWAN"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by inthewayboy on 2010-04-15
Ok, so I'm trying to setup a standalone Ubuntu Server running Apache2...it's gonna be a development web server. The problem I'm having is getting all the NICs to play nice.

I have two WAN's (T1 & DSL), and one private network. I want this box to be attached to all three as such:

eth0=LAN
eth1=T1
eth2=DSL

The reason for the two WAN's isn't for redundancy as much as monitoring. I want to be able to hit the same server through different ISP's for several reasons. I have two different FQDN's created, one for each interface.

So I would like either FQDN to serve up the same content. I need eth0 so I can get at it from my private LAN.

What do I need to do to make this work? eth1 and eth2 don't need to touch the private LAN if that helps any. Both eth1 and eth2 are static IP's coming straight from their respective modems, no firewall is between them.

Thanx in advance!!!

---


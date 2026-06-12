---
title: "bind9 forwarding/caching DNS for VPN"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by smashed.pumpkin on 2010-01-06
Hi, I wonder if someone could tell me if what i'm trying to do is possible:


I have Ubuntu 9.10 PC on my home network acting as a VPN gateway. It is using vpnc & iptables to provide access to the remote network - other computers on my local network have routing rules in place to go via the Ubuntu gateway if trying to reach an IP on the remote network. 

This works just fine, except DNS lookups for names on the remote network don't work.


I'm trying to solve this by using Bind9 on the gateway, so it can act as DNS for the local network. I don't want to create excess VPN traffic or load on the remote DNS, so I want the gateway to forward the lookup to my ISPs DNS first and if the name is not found then try the remote network DNS. Is this possible, or is there another (better) way around this? 

The Bind9 configs seem to admit multiple DNSs, but use them in a failover sense - only using secondary DNSs when the first one in the list is not reachable at all.


Apologies if my terminology is off, networking is not my forte :)

---

### Post by i.r.id10t on 2010-01-06
Set your bind to be a slave of the one on the vpn, so it has a local copy

Then anything it doesn't find in its own db it can forward to your ISP

---


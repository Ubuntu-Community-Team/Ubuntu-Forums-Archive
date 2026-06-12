---
title: "Using NAT to map public ip addresses to internal ip addresses?"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by maynardplace on 2009-04-04
Hi Folks,

I am new to Ubuntu and iptables.  I have a Linux server, which is acting as a gateway between our school's network and a subnet of 6 additional Linux client boxes. My server has two NICs; eth0 is configured to connect to the school's network and eth1 connects to a switch, to which the 6 clients are also connected.  This works fine.  I am implementing masquerading, using the iptables command,

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

and that does what it is advertised to do.  It makes it look like all the packets from my six clients are really coming from my server, so far as the outside WWW is concerned.

But what I would like is to have my server act as a router.  That is, I would like to translate the six public external ip addresses (yes I have them) to six internal ip addresses on my subnet.  Of course, any packets returned by my local clients should have the public external addresses as return addresses too.  Is there a way I can do this?

Thanks.

---


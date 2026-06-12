---
title: "eth0 traffic coming in on eth1 and vise versa"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by tmfries on 2010-01-07
Need a little help with a problem. I have two interfaces configured with different ip addresses. See interfaces file below:

# The loopback network interface
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
   address 192.x.x.x
   netmask 255.255.255.240
   gateway 192.x.x.x

auto eth0:1
iface eth0:1 inet static
   address 192.x.x.x
   netmask 255.255.255.240
   gateway 192.x.x.x

auto eth1
iface eth1 inet static
   address 10.x.x.x
   netmask 255.255.255.240
   gateway 10.x.x.x

auto eth1:1
iface eth1:1 inet static
   address 10.x.x.x
   netmask 255.255.255.240
   gateway 10.x.x.x

So the problem I am having is when I do a "tcpdump -nlv -i eth0 port 80" and hit my website I don't see any traffic but the website is displayed successfully. Through some troubleshooting I figured out that it is coming in on eth1. And when I hit the website on eth1 (different site) it comes in on eth0. I don't even know how this is possible. Both interfaces are connected to a hub instead of separate switches. Could that be screwing me up?

192.x.x.x and 10.x.x.x are used as an example but in my configuration they are actually my external interfaces and I use iptables to filter/route traffic to my internal suite. 

Anyone run into a problem like this before?

---

### Post by puppywhacker on 2010-01-07
IP uses per definition asynchronous routing, the routing table per node (hop-by-hop) decides where to route over. if you look at the route table you will see which path the packets will take.

---

### Post by tmfries on 2010-01-07
so I did an "ip route list"

default via x.x.x.x dev eth0  metric 100

do I need to add "src x.x.x.x" to get the traffic on the right interface?

---

### Post by puppywhacker on 2010-01-07
to be honest I don't really know what you are looking for but if it is synchronous routing where packets on the incoming link also go out on the outgoing link, I think you want some "ip rule"

[http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html)

---

### Post by tmfries on 2010-01-07
thanks for the help. I'll take a look and post back if I can't figure it out.

---


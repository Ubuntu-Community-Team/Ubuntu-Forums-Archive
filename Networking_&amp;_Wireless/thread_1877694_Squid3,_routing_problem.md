---
title: "Squid3, routing problem"
date: 2011-11-08
forum: Networking &amp; Wireless
---

### Post by albanderuaz on 2011-11-08
Hi everyone!

Ok, So I have two squid proxies on two different machines, PC1 and PC2.
PC2 is registered as being a parent cache in PC1, and PC2 has the internet connection. Proxies settings are set in internet browsers as pointing to PC1. Everything works. The problem is that a pc cannot access local machines: let's say PC3 is hosting a web server, and PC4 wants to connect to PC3 via http, unfortunately the connection goes through the squid proxies because of the proxy setting. Would it be possible to tell squid not to forward connections pointing to LAN machines?
A possible solution would be to configure the web browser in order to bypass the proxy for local addresses, but there are too many machines to do so in my network.

I tried to use iptables, but I didn't manage bypass squid for connections whose destinations are in the LAN

Many thanks for your help!

---


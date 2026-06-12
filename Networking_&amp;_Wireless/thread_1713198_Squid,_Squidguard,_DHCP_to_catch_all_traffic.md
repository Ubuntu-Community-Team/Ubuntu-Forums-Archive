---
title: "Squid, Squidguard, DHCP to catch all traffic"
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by iambud on 2011-03-23
I currently have squid and a DHCP server setup on a box. I want it to catch all traffic on the network and have squidguard filter it. I can currently have the browser point to the proxy and have it work. I don't want that. I want everyone who connects to the network wirelessly, and hardwired to go through the squid box. I've searched and have tried many things to get this to work. I've tried changing the iptables 

iptables -t nat -A OUTPUT -m tcp -p tcp --dport 80 -j REDIRECT --to ports 3128

Still to no aval. Im lost:confused:

---


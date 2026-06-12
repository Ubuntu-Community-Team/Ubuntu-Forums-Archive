---
title: "vtun  VPN routing issue"
date: 2011-04-02
forum: Networking &amp; Wireless
---

### Post by alex.stapleton on 2011-04-02
I have a vtun tunnel (interface tun0) between my home server (running ubuntu 10.10) and my VPS (running Debian stable.) The VPS has iptables configured to redirect port 60443 to port 443 on my home server.

The packets get from the VPS to the home server on port 443 but their source address is kept intact. So it's seeing packets from Internet addresses on an interface that's only meant to have a single, privately addressed host at the end of it. The packets then get dropped, presumably because my home server doesn't like the source addresses.

So basically. How can I tell my Ubuntu home server that tun0 is meant to have crazy Internet addresses sending data down it? Presumably I need to use the ip route command but I have no idea exactly what I need to do with it.

---


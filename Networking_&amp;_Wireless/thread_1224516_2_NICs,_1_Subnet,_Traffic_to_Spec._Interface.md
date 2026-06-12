---
title: "2 NICs, 1 Subnet, Traffic to Spec. Interface"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by DGortze380 on 2009-07-27
I'm in the process of working this out myself, but any advice is certainly appreciated... it will cut my time down significantly.

I have a server, running a number of services (ssh, ftp, apache (multiple), darwin streaming server).

The server is multi-homed, it has 2 NICs.
Both NICs are on the same subnet, and must remain on the same subnet.

Due to (suspected) bandwidth issues, I need the server to route all traffic for the streaming server through a particular interface.

I believe this is possible through some iptables rules...?

---


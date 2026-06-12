---
title: "Host Based NAT?"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by linorics on 2010-02-12
Hi there I'm running A Linux based firewall/router with DHCP NAT and DNS.

I can only have one public ip address. I have two servers running identical programs, each using port 9352(And I can change that).

Server a.domain.com | Server b.domain.com

My client program want to connect to a.domain.com and b.domain.com using port 9352(Also can't be changed... very stupid program...).

So is there a way to tell a router that if the request is for a.domain.com forward to host a on the nat 192.168.0.50, and b.domain.com to host b 192.168.0.60?

I have no idea if this is possible, but i would think there is something that I could do.

---


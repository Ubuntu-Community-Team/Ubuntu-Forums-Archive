---
title: "Accessing HTTP secure from Windows client via pptpd based Linux VPN server"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by Zhuoxi on 2010-12-16
Server side:
pptpd + iptables

ipv4_forwarding:
iptables -t nat -A POSTROUTING -j MASQUERADE
============================================================
Client side:
Windows 7 64bit Ent., and Windows XP, pptp protocol client.

With this configuration HTTP sites are accessible, but HTTP secure sites can not accessed.
============================================================
Client side:
Linux with pptp protocol client.

With this configuration both HTTP and HTTP secure sites can be accessed.
============================================================
Questions:

What is the difference between Windows and Linux clients configuration? Is it necessary to build An l2tp based VPN server on to access HTTP secure site on my Windows client?

Thanks.

---


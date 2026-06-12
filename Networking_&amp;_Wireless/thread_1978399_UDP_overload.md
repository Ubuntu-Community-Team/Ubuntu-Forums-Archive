---
title: "UDP overload"
date: 2012-05-11
forum: Networking &amp; Wireless
---

### Post by rfictus on 2012-05-11
When I connect to some foreign network, Ubuntu 12.04, my network connection goes haywire. Firewall gives constant string of UDP messages.

i.e.
dnsmasq UDP Port 24552
dnsmasq UDP Port 39502
dnsmasq UDP Port 59295
dnsmasq UDP Port 69320
dnsmasq UDP Port 70492

etc etc..

Network connection remains but cannot connect to foreign machines anymore. The message string continues..

I get my connection working again by disabling wireless adapter and enabling it. Even then, takes a few minutes before firewall returns UDP message string again and accees to foreign machines is denied.

I have 'firewall' installed if that helps. I get the string even when the firewall, iptables and ufw are turned off.

Clues anyone?

---


---
title: "IPSec VPN problems"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by jake247 on 2011-03-08
Hi guys and girls!

Trying to establish an ipsec vpn between two machines (network to network) and just can't seem to crack it.

Both machines are situated behind an ISP managed router using their default gateways and public ip addresses on eth0 (One AboveNet, one Tata).

The other interfaces (both empty) are assigned 192.168.100.1 && 192.168.200.1

This is where my questions start, try as I might I'm not able to get them to shoot packets between.

I'm at an end, how should I be configuring this? Neither eth1 is attached to anything, just assigned 192.168.200.1 and 192.168.100.1, I've been using those IP addresses as a default gateway for the ipsec setup and etc also.

Should I be using iptables to do some form of NAT? I use --list and they're completely empty and I'm unsure how traffic would be passed between interfaces although in sysctl ip_forward is enabled. :s

---

### Post by jake247 on 2011-03-08
Given up on that now, implemented PPTP!

---


---
title: "IP Tables - Forcing user to use VPN"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by mojo6911 on 2011-03-08
Hello,

I would like to make a user's executed programs only run through my VPN tun0, except for port 8082, which I would like to be connected at all times to eth0. I have tried to use IP Tables, but suck at it. user would be the user I want to control.

iptables -A OUTPUT -o tun0 -m owner --uid-owner user -j ACCEPT 
iptables -A OUTPUT -o eth0 -m owner --uid-owner user -p -tcp --dport 8082 -j ACCEPT
iptables -A OUTPUT -o eth0 -m owner --uid-owner user -j REJECT

---


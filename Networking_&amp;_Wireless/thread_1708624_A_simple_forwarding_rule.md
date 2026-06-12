---
title: "A simple forwarding rule?"
date: 2011-03-16
forum: Networking &amp; Wireless
---

### Post by nkae100 on 2011-03-16
> iptables -A FORWARD -p tcp -i INTERNET --dport 80 -d 192.168.56.101 -j ACCEPT

I've been given this command which allows me to forward incoming port 25 connections to 192.168.56.101. What I was wondering though is if its possible to specify a port for the destination IP address?

I want to forward connections from port 25 to 192.168.56.101 on port 2525

---


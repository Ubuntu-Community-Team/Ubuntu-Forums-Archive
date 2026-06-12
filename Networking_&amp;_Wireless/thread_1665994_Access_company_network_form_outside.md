---
title: "Access company network form outside"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by Amit Lonare on 2011-01-13
we hav one of our client want access our company computer from outside network and all our computers are under proxy server therefore all computers have limited access so one of the limited access computer, client has to access from outside. so we want this computer should remain under proxy server as well as accessible from outside network

---

### Post by cariboo on 2011-01-13
Moved to a thread of it's own, as it had nothing to do with the thread it was in.

---

### Post by Farrukhjon on 2011-01-13
[SIZE=3][B]Organize by means of NAT iptables: about so 
 ip tables-t nat PREROITING-A s (source ip)-d (destination ip) in - dport (your port need) - to-destination (ip)
[/B][/SIZE]

---

### Post by sj1410 on 2011-01-13
> **Amit Lonare said:**
> we hav one of our client want access our company computer from outside network and all our computers are under proxy server therefore all computers have limited access so one of the limited access computer, client has to access from outside. so we want this computer should remain under proxy server as well as accessible from outside network

what firewall or router you have. you need to do port forwarding.

---


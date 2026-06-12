---
title: "iptables that allow IRC"
date: 2013-03-15
forum: Networking &amp; Wireless
---

### Post by duanedesign on 2013-03-15
I am having trouble connecting to IRC(freenode) because of my iptables.

I tried the following
*iptables -A INPUT -p tcp --syn --destination-port 6697 -j ACCEPT*
*iptables -A OUTPUT -p tcp -m tcp --dport 6697 -j ACCEPT*
(i use port 6697 because I connect using SSL)

And for pings:
*iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT*

Any help would be greatly appreciatted.

---

### Post by slickymaster on 2013-03-15
Have you already tried using ports 7000 or 7070?

---


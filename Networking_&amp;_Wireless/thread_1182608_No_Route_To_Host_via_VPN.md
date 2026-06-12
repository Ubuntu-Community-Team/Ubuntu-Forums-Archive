---
title: "No Route To Host via VPN"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by ToshiBoy on 2009-06-09
Ok, so once upon a time I had a perfectly working 7.04 system with VPN to SBS 2003. I've spent endless days trawling through forums to find out how to connect 8.04, then 8.10, now 9.04. In the end, I just went methodically through all the options and finally I have a connection. Great. 

But now, I'm connected and can't do anything. Pings tell me that the destination on the remote network is unreachable. ssh returns a "no route to host". The routing table as per route is empty. I've gone through a number of forums again, but can't seem to find any method to make this work. I guess it has to do with the routing under the IPv4 options?

According to ifconfig, I am being allocated an IP address on the remote network... so what am I doing wrong?

---


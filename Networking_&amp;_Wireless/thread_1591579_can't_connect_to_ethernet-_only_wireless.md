---
title: "can't connect to ethernet- only wireless"
date: 2010-10-09
forum: Networking &amp; Wireless
---

### Post by hawkmcd on 2010-10-09
I'm a new Ubuntu user. My computer is picking up some wireless signals but I would like it to use the wired ethernet connection. It recognizes the ethernet connection and my MAC address, but it will not connect to it, so I'm stuck with a slow wireless connection. I tried to download wicd, but it won't go through since it's too slow.
 
Any ideas?

---

### Post by Iowan on 2010-10-09
Does **ifconfig -a** show eth0 with an IP address?  If you know the router's address, you might try a static address (at least short-term...).

---


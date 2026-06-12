---
title: "connecting from a far"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by johnh10000 on 2009-06-07
HI. I just upgraded from 8.10 to 9.04. ok i broke the network settings some how.

Anyway connect through a router to the net fine (now)
got a dyndns, thingy asked router to give me the same ip to all local networked machines. www, and ftp work fine locally. but connection closed by host when I ftp, and error msg saying looks like it's there but I can't get in, on www.

I know it's a firewall problem.  I use use lokkit but it seems I can't any more any recomendations?

---

### Post by superprash2003 on 2009-06-08
did you use the dyndns address to access from a local computer in your network or from a computer outside your network? post output of sudo iptables -L , use this online port scanner to see if port 80,21 are open [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---


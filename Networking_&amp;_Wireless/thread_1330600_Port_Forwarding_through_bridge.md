---
title: "Port Forwarding through bridge"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by pepsifx357 on 2009-11-18
Hey guys, here is my setup and problem.

Internet -> Router 1 "netgear wnr2000" (10.10.10.1) -> wireless Bridge Router "DD-WRT" (10.10.10.200) -> Server (10.10.10.202)

I need to port forward port 80 to my server, how do I do this.  I've played around with it, but I've figured out I have no clue what I am doing.  

P.S. I am using DDNS service if that makes any difference.

---

### Post by puppywhacker on 2009-11-18
you have to set the portforward on Router 1 "netgear wnr2000" and towards 10.10.10.202. You'll be forwarding TCP port 80 on L4. YMMV but this should not be influenced by internal routing (IP on L3) or bridging (Ethernet on L2).

---


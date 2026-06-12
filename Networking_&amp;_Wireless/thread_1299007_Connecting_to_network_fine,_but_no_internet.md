---
title: "Connecting to network fine, but no internet"
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by antieuclid on 2009-10-23
I'm running a fairly vintage Dell laptop with an old 802.11b wireless card. After having to play around with manual IP assignment, I did eventually get it connected to the network. I can access the router configuration page in firefox without problems. But it still won't let me on the internet in general. The router is a D-link DIR-615. Anyone have any hints?

---

### Post by chili555 on 2009-10-23
> After having to play around with manual IP assignmentA manual IP assignment or static, requires that you, and not the router, supply the DNS nameserver. Did you remember to do that? You can edit */etc/resolv.conf* and use the address of your router, thus:```
nameserver 192.168.1.1
```Substitute your router's address here.

---


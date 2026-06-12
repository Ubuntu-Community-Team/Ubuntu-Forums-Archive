---
title: "Better use of ifconfig?"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by zozza on 2010-01-04
Using ipconfig /all in XP I obtain the IP, Subnet, Gateway, and DNS.

Using ifconfig in Ubuntu I just get the IP and broadcast.  Is there a better command than ifconfig that can be used to obtain the same kind of details as ipconfig /all gets?

Thanks.

---

### Post by diesch on 2010-01-04
```
route
``` shows you the routing table
```
cat /etc/resolv.conf
``` the DNS settings

---


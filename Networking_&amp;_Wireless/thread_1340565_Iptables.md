---
title: "Iptables"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by justifier on 2009-11-28
How do i route all trafic from port 8025 to 25 to enable smtp to work on 8025. I just need it to be on the same server. (my isp filter port 25) 

Many thanks 

Adam Lowe

---

### Post by Brandon Williams on 2009-11-29
This will handle destination NAT for incoming tcp traffic to port 8025 on interface eth1, sending it to port 25 at the same destination address.

```
$ sudo iptables -t nat -I PREROUTING -p tcp -i eth1 --dport 8025 -j DNAT --to=:25
```

---


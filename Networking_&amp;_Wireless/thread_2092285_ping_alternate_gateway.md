---
title: "ping alternate gateway"
date: 2012-12-07
forum: Networking &amp; Wireless
---

### Post by tinkerbox on 2012-12-07
Hi, 

I been googling for few hours and test some commands or scripts with no luck. Hopefully someone here will be able to help me =)

I have single network card: 192.168.0.1 / 255.255.255.0
and I have to gateway within same network

gateway 1: 192.168.0.101
gateway 2: 192.168.0.102

Using this line, I manage to load balance my internet connection this does work fine
```
/bin/ip route add default scope global nexthop via 192.168.0.101 dev eth0 weight 1 nexthop via 192.168.0.102 dev eth0 weight 1
```

```
# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0    *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.101  0.0.0.0         UG    0      0        0 eth0
```


My problem is, when I reset or one of my ISP is down, if one of my application is using 192.168.0.101 as gateway it will not chg to alternate gateway: 192.168.0.102

I need a way to check or ping thru selected gateway to check if the ISP is online. If I can to this i can delete offline gateway and set alternate gateway as default...

Any ideas?

---

### Post by tinkerbox on 2012-12-11
Bump...

---

### Post by tinkerbox on 2012-12-14
Pls anyone? Help pls

---

### Post by tinkerbox on 2012-12-21
sigh...

---


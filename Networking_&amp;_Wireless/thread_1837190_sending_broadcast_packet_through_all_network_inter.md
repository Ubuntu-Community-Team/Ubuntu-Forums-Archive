---
title: "sending broadcast packet through all network interfaces"
date: 2011-09-01
forum: Networking &amp; Wireless
---

### Post by mastupristi on 2011-09-01
hi,

I have two network interfaces, eth0 (192.168.1.0/24) e eth3 (192.168.15.0/24)
and the routing table is:

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.15.0    0.0.0.0         255.255.255.0   U     1      0        0 eth3
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
```

I have a program that send some broadcast packets, but them are outputed only on eth0

How to configure network interfaces to be able to output broadcast on both interfaces?

thanks

---


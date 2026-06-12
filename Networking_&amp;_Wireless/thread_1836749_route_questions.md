---
title: "route questions"
date: 2011-08-31
forum: Networking &amp; Wireless
---

### Post by ant2ne on 2011-08-31
```
Nedimare-01:/home/ant2ne# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.4.1.0        vmhost.cygnehom 255.255.255.0   UG    0      0        0 eth0
10.1.1.0        vmhost.cygnehom 255.255.255.0   UG    0      0        0 eth0
10.1.1.0        *               255.255.255.0   U     0      0        0 eth0
default         vmhost.cygnehom 0.0.0.0         UG    0      0        0 eth0

```

Q1, how to i NOT resolve hostnames for route? I don't want to rely on my DNS to push packets.

Q2 what is up with the 10.1.1.0s. Why do I have 2? Which one do I need. This devices interface is on the 10.1.1.7 network.

---


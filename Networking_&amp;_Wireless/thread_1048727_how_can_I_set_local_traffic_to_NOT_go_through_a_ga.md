---
title: "how can I set local traffic to NOT go through a gateway?"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by Thasp on 2009-01-23
Present routing: 


```
# ip r s
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.248
10.10.10.0/24 dev eth1  proto kernel  scope link  src 10.10.10.2
default via 10.10.10.1 dev eth1

```

```
# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
10.10.10.0      0.0.0.0         255.255.255.0   U         0 0          0 eth1
0.0.0.0         10.10.10.1      0.0.0.0         UG        0 0          0 eth1

```

```
# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.10.10.0      0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         10.10.10.1      0.0.0.0         UG    0      0        0 eth1

```

I think local traffic is trying to go through a gateway, instead of directly connecting to another machine on the network.

---

### Post by Thasp on 2009-01-24
bump

---


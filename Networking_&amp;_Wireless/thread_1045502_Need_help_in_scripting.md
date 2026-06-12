---
title: "Need help in scripting"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by stepper on 2009-01-20
I need help with putting together a script that will change route tables in order to change which interface to use to connect to internet.

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```

I normally do the following to interchange interfaces:
1. sudo ip route del default via 0.0.0.0 dev eth1
2. sudo ip route add default via 0.0.0.0 dev ppp0

and vice versa to change interfaces. Is it possible to put this in a script and run it without typing the two above commands in the terminal?

---


---
title: "Routing problem with 3 machines"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by bluefox on 2006-07-11
This is my setup, all machines have the same Ubuntu configuration.
[LIST=1]
[*]Ubuntu 6.0.6
[*]iptables removed
[*]Static IP, mask 255.255.255.0
[*]ipv4 forwarding enabled (/proc/sys/net/ipv4/ip_forward = 1)
[*]Qugga is used, ripd & zebra enabled
[/LIST]
```

   M1 <---------------------> M2 <--------------------> M3
192.168.98.1      192.168.98.2 192.168.101.1      192.168.101.2

route -n for M1:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.98.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.101.0   192.168.98.2    255.255.255.0   UG    3      0        0 eth0

route -n for M2:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.98.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.101.0   0.0.0.0         255.255.255.0   U     0      0        0 eth1

route -n for M3:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.98.0    192.168.101.2   255.255.255.0   UG    3      0        0 eth0
192.168.101.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
```
Problem: I can ping between M1 & M2, M2 and M3, but I can't ping from M1 to M3 or M3 to M1 directly.. Anyeone know any possible cause of this?

---

### Post by joft on 2006-07-11
Hi,

according to your static IP settings (first two lines of given code), there are at least two things wrong with your routing tables:

1. The subnet between M1 and M2 is 192.168.89.0 and NOT 192.168.98.0 . You have to correct that in the routing table of all 3 machines, though I suspect that this is a typo in your posting?

2. In M3's routing table is should be

```

192.168.89.0    192.168.101.1   255.255.255.0   UG    3      0        0 eth0
```

instead of:

```

192.168.98.0    192.168.101.2   255.255.255.0   UG    3      0        0 eth0
```

---

### Post by bluefox on 2006-07-11
Yeah sorry, typo in the setup graph.. here's the correct setup.
```

   M1 <---------------------> M2 <--------------------> M3
192.168.98.1      192.168.98.2 192.168.101.1      192.168.101.2

```

---

### Post by bluefox on 2006-07-12
Anyone know what might be the cause of this?

---

### Post by joft on 2006-07-12
Hi,

did you correct the routing table of M3 or was it a typo, too? (See my first post, 101.1 instead of 101.2).

---

### Post by MrHorus on 2006-07-12
The gateway on M3 should be 192.168.101.1 as this is the IP of the upstream router, not the local IP of 192.168.101.2.

---

### Post by mips on 2006-07-12
See above, alternatively try Firestarter.

---


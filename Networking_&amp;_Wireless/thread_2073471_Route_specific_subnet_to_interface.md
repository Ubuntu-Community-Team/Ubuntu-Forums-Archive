---
title: "Route specific subnet to interface"
date: 2012-10-19
forum: Networking &amp; Wireless
---

### Post by wolfsburg18 on 2012-10-19
Problem: Direct all traffic except for specific subnet (10.168.201.0/24) to eth0 and all remaining traffic to eth1.

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:ac:6f:42:22:a4  
          inet addr:10.168.201.93  Bcast:10.168.201.255  Mask:255.255.255.0
          inet6 addr: fe80::baac:6fff:fe42:22a4/64 Scope:Link

eth1      Link encap:Ethernet  HWaddr 64:70:02:09:32:f6  
          inet addr:10.0.1.49  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: 2601:1:b300:4:6670:2ff:fe09:32f6/64 Scope:Global
          inet6 addr: fe80::6670:2ff:fe09:32f6/64 Scope:Link
 
``````

$ route -n
Kernel IP routing table
Destination     Gateway              Genmask            Flags   Metric   Ref    Use Iface
10.168.201.0    0.0.0.0               255.255.255.0    U        1          0        0 eth0
10.0.1.0           0.0.0.0               255.255.255.0    U        0          0        0 eth1
169.254.0.0      0.0.0.0               255.255.0.0       U        1000     0        0 eth0
0.0.0.0            10.168.201.254    0.0.0.0              UG      0          0        0 eth0
0.0.0.0            10.0.1.1              0.0.0.0              UG      100       0        0 eth1


```I  have the following code which should direct all traffic to return to  the same port it is from so actions on the internet should not have an  issue.  Please correct me if I am wrong.
 ```

ip route add 10.168.201.0/24 dev eth0 src 10.168.201.93 table local1
ip route add default via 10.168.201.254 table local1

ip route add 10.0.1.0/24 dev eth1 src 10.0.1.49 table inet
ip route add default via 10.0.1.1 table inet

ip route add 10.168.201.0/24 dev eth0 src 10.168.201.93
ip route add 10.0.1.0/24 dev eth1 src 10.0.1.49
ip route add default via 10.0.1.1

ip rule add from 10.168.201.93 table local1
ip rule add from 10.0.1.49 table inet

```

---

### Post by efflandt on 2012-10-19
I am not familiar with ip route (I just do static routing for subnets of subnets if necessary and have not used metrics).    So I might not understand what you are attempting to beyond your description.

But if you only want eth0 to handle 10.168.201.0/24, why have you set 2 default gateways including eth0 with lower metric to 10.168.201.254 (what device is at that IP and/or what network is on the other side of that router)?  Shouldn't you end up with only 1 default gateway (and maybe zero the metric for it)?

```
$ route -n
Kernel IP routing table
Destination     Gateway              Genmask            Flags   Metric   Ref    Use Iface
10.168.201.0    0.0.0.0              255.255.255.0      U       1        0        0 eth0
10.0.1.0        0.0.0.0              255.255.255.0      U       0        0        0 eth1
169.254.0.0     0.0.0.0              255.255.0.0        U       1000     0        0 eth0
0.0.0.0         10.0.1.1             0.0.0.0            UG      100      0        0 eth1
```

---

### Post by wolfsburg18 on 2012-10-24
I am still trying to understand the routing table so changes can be made to to provide the machine appropriate connectivity.

Two networks
Eth0: connectivity to an in home network with file server, printer and other devices.
Eth1: connectivity to public internet.

I need some help on the commands to clear the current routing table and configure it for Eth0 for only the subnet of 10.168.201.254/24 and Eth1 for all other traffic.

---

### Post by wolfsburg18 on 2012-10-24
Since someone else my run into this issue or something similar, I believe I have this resolved however not sure if this is the best solution.

View Network route
```

$route -n

```

Add a new default route
```

$sudo route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.0.1.1 eth0

```

Remove the old default route
```

$sudo route delete -net 0.0.0.0 netmask 0.0.0.0 gw 10.168.201.254 eth1

```

Verify changes are present
```

route -n

```

---


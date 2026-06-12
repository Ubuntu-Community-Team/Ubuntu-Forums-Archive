---
title: "enhanced routing within vm"
date: 2010-06-18
forum: Networking &amp; Wireless
---

### Post by tekknokrat on 2010-06-18
I have a vm (kvm) which connects to 3 outside bridges via tap.

The ip setup is splitted in different subnets (45.0/24, 46.0/24 and 178.0/24):
```

2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 40:61:86:00:45:01 brd ff:ff:ff:ff:ff:ff
    inet 10.0.45.10/24 brd 10.0.45.255 scope global eth0
    inet 10.0.45.101/32 scope global secondary eth0
    inet 10.0.45.102/32 scope global secondary eth0
    inet 10.0.45.103/32 scope global secondary eth0
    inet 10.0.45.104/32 scope global secondary eth0
    inet 10.0.45.105/32 scope global secondary eth0
    inet 10.0.45.110/32 scope global secondary eth0
    inet6 fe80::4261:86ff:fe00:4501/64 scope link
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 40:61:86:00:46:02 brd ff:ff:ff:ff:ff:ff
    inet 10.0.46.11/24 brd 10.0.46.255 scope global eth1
    inet 10.0.46.101/32 scope global secondary eth1
    inet6 fe80::4261:86ff:fe00:4602/64 scope link
       valid_lft forever preferred_lft forever
4: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 40:61:86:00:b2:01 brd ff:ff:ff:ff:ff:ff
    inet 10.0.178.11/24 brd 10.0.178.255 scope global eth2
    inet 10.0.178.105/32 scope global secondary eth2
    inet6 fe80::4261:86ff:fe00:b201/64 scope link
       valid_lft forever preferred_lft forever

```

Default Gateway is 10.0.45.1. Outside the VM are different public IPs natted (DNAT) to this internal ips.
This works, but only for 10.0.45.0/24. I want this to work for the 10.0.178.0/24 network too. Especially there is a DNAT rule (shorewall rule file) that works in this case (45er subnet):

```

Web(DNAT)       net     loc:10.0.45.105         tcp             -               -               XX.XX.XX.178

```

But does not work in this case:

```

Web(DNAT)       net     loc:10.0.178.105         tcp             -               -               XX.XX.XX.178

```


The Routing setup:
```

# ip route
10.0.178.0/24 dev eth2  scope link  src 10.0.178.105 
10.0.45.0/24 dev eth0  proto kernel  scope link  src 10.0.45.10 
10.0.46.0/24 dev eth1  proto kernel  scope link  src 10.0.46.11 
default via 10.0.45.1 dev eth0  metric 100

```

```

# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.178.0      0.0.0.0         255.255.255.0   U     0      0        0 eth2
10.0.45.0       0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.0.46.0       0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         10.0.45.1       0.0.0.0         UG    100    0        0 eth0

```

I tried this src based route approach
```

ip route add 10.0.178.1 dev eth2 src 10.0.178.105

```

and also src based with multicast routing
```

ip route add 10.0.178.0/24 dev eth2 src 10.0.178.105

```

Both without success. Adding additional default route with src also breaks the default route
```

# ip route add default via 10.0.178.1 dev eth2 src 10.0.178.105

```

From the host server i can ping and connect fine to 10.0.178.105.
Any hint how to make DNAT to this last ip address work?
Please tell me if you need further details!

---


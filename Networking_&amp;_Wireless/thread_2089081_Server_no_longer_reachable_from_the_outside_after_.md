---
title: "Server no longer reachable from the outside after second interface is configured"
date: 2012-11-28
forum: Networking &amp; Wireless
---

### Post by devaube on 2012-11-28
Hey everyone,

I have a server that should be connected to two networks. One where it is connected via a router to the internet and another one connected to a local network. I make certain ports of the server available in the internet, via port-forwarding.
As soon as I configure the second interface (eth1), which has a static IP configuration, connection attempts from the internet fail. The ports are open but no data is transferred. In the network of the router the server is still reachable normally.

Here is the /etc/network/interfaces of the server:
```
## This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The secondary network interface
auto eth1
iface eth1 inet static
  address 192.168.100.3
  gateway 192.168.100.1
  netmask 255.255.255.0
  network 192.168.100.0
  broadcast 192.168.100.255
```

route -n:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.100.1   0.0.0.0         UG    0      0        0 eth1
192.168.3.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.100.0   0.0.0.0         255.255.255.0   U     0      0        0 eth1
```

Thank you for any suggestions.

---


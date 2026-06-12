---
title: "speed to cross network"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by wcorey on 2011-02-21
I have a system setup where one instance of Ubuntu server has two eths, 0 and 1. Eth0 is on the 192.168.0.0 network and eth1 is on the 192.168.1.0 network

From a third machine on the 192.168.0.0 network I can shell into the first server mentioned (192.168.0.3) in sub second time.However once on the 192.168.0.3 machine issuing an ssh to the 192.168.1.2 machine takes somewhere on the order of 10 seconds to get a prompt for password.

Here is the route list from the machine with two eths:

Kernel IP routing table
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth0

```

Here is the interface definition 


```
# This file describes the network interfaces available on your system
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
address 192.168.1.1
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0
```


I can not conceive of what would be causing the performance degradation on ssh.

TIA,
Walt

---


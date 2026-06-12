---
title: "no connectivity when using bridging"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by ziphyre on 2008-12-08
Hello,

I got two nics (eth0, eth1) and I want to create a bridge with eth1 for my virtual machines, and use eth0 as my default interface to internet. But when br0 is up, I can't connect to outside world, if I ifdown br0, than everything's OK.

Here is my interfaces file:
```
# The loopback network interface
auto lo
iface lo inet loopback

# 1st network interface
auto eth0
iface eth0 inet static
        address 192.168.1.10
        netmask 255.255.255.0
        gateway 192.168.1.1

# 2nd network interface
auto eth1
iface eth1 inet manual

# 1st bridge for vm
auto br0
iface br0 inet static
        address 192.168.1.11
        netmask 255.255.255.0
        gateway 192.168.1.1
        bridge_ports eth1
        bridge_fd    9
        bridge_hello 2
        bridge_maxage 12
        bridge_stf   off
```

Any advices?

---

### Post by ziphyre on 2008-12-08
another information,
when br0 is down:
```
$ route
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.122.0   *               255.255.255.0   U     0      0        0 vnet0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
```

when br0 is up:
```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 br0
192.168.122.0   *               255.255.255.0   U     0      0        0 vnet0
default         192.168.1.1     0.0.0.0         UG    100    0        0 br0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
```

And it hangs after the third line before printing the default routes for 5 secs...

---

### Post by jmoorse on 2008-12-08
Just a though: try adjusting the metric for br0

add:
up ifmetric br0 100

To your br0 interface config in /etc/interfaces

It appears Ubuntu is choosing that routing entry by default instead of using your eth0 as the gateway.

---

### Post by ziphyre on 2008-12-08
Thanks.
It did the trick

---


---
title: "wrong metric in routes for 4 interfaces"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2011-04-27
On a server with 4 network interfaces, sometimes not all 4 are plugged in.  All 4 interfaces have the same IP address.  Sometimes the machine cannot access the local LAN, but can access the internet via a router on the local LAN, after a reboot.  What I find is that the routing table looks like this:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.30.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eth0
172.30.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eth1
172.30.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eth2
172.30.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eth3
0.0.0.0         172.30.0.2      0.0.0.0         UG    1      0        0 eth0
0.0.0.0         172.30.0.2      0.0.0.0         UG    2      0        0 eth1
0.0.0.0         172.30.0.2      0.0.0.0         UG    3      0        0 eth2
0.0.0.0         172.30.0.2      0.0.0.0         UG    4      0        0 eth3
```On the console I cannot reach any local host, but I can reach internet hosts.  Pinging the gateway router 172.30.0.2 gets no answer.  When I manually change it to this:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.30.0.0      0.0.0.0         255.255.0.0     U     1      0        0 eth0
172.30.0.0      0.0.0.0         255.255.0.0     U     2      0        0 eth1
172.30.0.0      0.0.0.0         255.255.0.0     U     3      0        0 eth2
172.30.0.0      0.0.0.0         255.255.0.0     U     4      0        0 eth3
0.0.0.0         172.30.0.2      0.0.0.0         UG    1      0        0 eth0
0.0.0.0         172.30.0.2      0.0.0.0         UG    2      0        0 eth1
0.0.0.0         172.30.0.2      0.0.0.0         UG    3      0        0 eth2
0.0.0.0         172.30.0.2      0.0.0.0         UG    4      0        0 eth3
```then all is well (can ping local hosts including the gateway router).  I do have metric specified in the /etc/network/interfaces file like this:

```
auto lo
iface lo inet loopback
               
auto eth0
iface eth0 inet static
        address 172.30.16.8
        netmask 255.255.0.0
        network 172.30.0.0
        broadcast 172.30.255.255
        metric 1

auto eth1
iface eth1 inet static
        address 172.30.16.8
        netmask 255.255.0.0
        network 172.30.0.0
        broadcast 172.30.255.255
        metric 2

auto eth2
iface eth2 inet static
        address 172.30.16.8
        netmask 255.255.0.0
        network 172.30.0.0
        broadcast 172.30.255.255
        metric 3

auto eth3
iface eth3 inet static
        address 172.30.16.8
        netmask 255.255.0.0
        network 172.30.0.0
        broadcast 172.30.255.255
        metric 4
```Apparently that metric setting applies only to the gateway route, not the LAN route.  Is there a way to specify the LAN route metric, too?

---

### Post by Skaperen on 2011-04-29
Does anyone know where within the Ubuntu startup that the network routes are put into place?

---


---
title: "Ubuntu and VmWare network mess"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by nicolasdiogo on 2010-03-05
Hi,

i have installed a ubuntu server 9.10 x64 with VmWare server.

i now have a guest ubuntu hardy that i am trying to setup as the gateway for the whole network.

by i am getting some really annoying problems with the network setup.

the host has three NIC
eth0 - connected to a router(internet)

eth1 - internal network
eth2 - internal network

the ip on router is 192.168.1.1 (defualt)
my eth0 has ip 192.168.1.215

and it works fine when i need to update and install packages

however, none of my guests can connect to my internal network.

the ip for internal network are as follows:
eth1 - 172.16.0.11
eth2 - 172.16.0.12

here is the output of route -rn
```

10.0.100.0      0.0.0.0         255.255.255.0   U     0      0        0 vmnet10
172.16.0.0      0.0.0.0         255.255.255.0   U     0      0        0 eth1
172.16.0.0      0.0.0.0         255.255.255.0   U     0      0        0 eth2
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
33.0.100.0      0.0.0.0         255.255.255.0   U     0      0        0 vmnet11
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         172.16.0.1      0.0.0.0         UG    100    0        0 eth2
0.0.0.0         172.16.0.1      0.0.0.0         UG    100    0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```


on the host this is the /etc/network/interfaces file:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0 eth1 eth2

iface lo inet loopback

iface eth0 inet static
        address 192.168.1.215
        netmask 255.255.255.0
        gateway 192.168.1.1


iface eth1 inet static
        address 172.16.0.11
        netmask 255.255.255.0

iface eth2 inet static
        address 172.16.0.12
        netmask 255.255.255.0

```


any suggestion will be much appreciated..

thanks,
if i try to

---


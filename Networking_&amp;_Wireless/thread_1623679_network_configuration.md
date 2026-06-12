---
title: "network configuration"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by siikaisz on 2010-11-16
[FONT=Arial]Today i moved from one dedicated server room to another and made network config according
```
ip: 94.101.224.182-94.101.224.187
mask 255.255.255.0 
gateway 94.101.224.1 
dns 94.101.224.2, 89.111.13.115 

```but problem is what from outside can ping and works only main IP 94.101.224.184, all other virtual interfaces don't work.

also if i ping 94.101.224.185 ip address from box what is in the same server room i get first time reply and all other unreachable:
[/FONT]```
Pinging 94.101.224.185 with 32 bytes of data:
Reply from 94.101.224.185: bytes=32 time<1ms TTL=64
Reply from 94.101.224.1: Destination host unreachable.
Reply from 94.101.224.1: Destination host unreachable.
Reply from 94.101.224.1: Destination host unreachable.

```[FONT=Arial]

my interface config:
[/FONT]```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth1 eth1:0 eth1:1 eth1:2 eth1:3 eth1:4
iface lo inet loopback

# The primary network interface
iface eth1 inet static
	address 94.101.224.184
	netmask 255.255.255.0
	network 94.101.224.0
	broadcast 94.101.224.255
	gateway 94.101.224.1
	dns-nameservers 94.101.230.2
	dns-search heaven.lv
iface eth1:0 inet static
	address 94.101.224.185
	netmask 255.255.255.0
	broadcast 94.101.224.255
	network 94.101.224.0

iface eth1:1 inet static
	address 94.101.224.186
	netmask 255.255.255.0
	broadcast 94.101.224.255
	network 94.101.224.0

iface eth1:2 inet static
	address 94.101.224.183
	netmask 255.255.255.0
	broadcast 94.101.224.255
	network 94.101.224.0

iface eth1:3 inet static
	address 94.101.224.187
	netmask 255.255.255.0
	broadcast 94.101.224.255
	network 94.101.224.0

iface eth1:4 inet static
	address 94.101.224.182
	netmask 255.255.255.0
	broadcast 94.101.224.255
	network 94.101.224.0

```[FONT=Arial]
[/FONT][FONT=Arial]Problem is in my NIC?
[/FONT][FONT=Arial]Problem is in my config?
[/FONT][FONT=Arial]Problem is in my dedicated server room router/gateway?[/FONT]

Thanks for Help ;)


Another usefull info
IFCONFIG
```
eth1      Link encap:Ethernet  HWaddr 00:21:91:f4:35:f9
          inet addr:94.101.224.184  Bcast:94.101.224.255  Mask:255.255.255.0
          inet6 addr: fe80::221:91ff:fef4:35f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4097998 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3534598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2028663048 (2.0 GB)  TX bytes:802487547 (802.4 MB)
          Interrupt:18 Base address:0xec00

eth1:0    Link encap:Ethernet  HWaddr 00:21:91:f4:35:f9
          inet addr:94.101.224.185  Bcast:94.101.224.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xec00

eth1:1    Link encap:Ethernet  HWaddr 00:21:91:f4:35:f9
          inet addr:94.101.224.186  Bcast:94.101.224.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xec00

eth1:2    Link encap:Ethernet  HWaddr 00:21:91:f4:35:f9
          inet addr:94.101.224.183  Bcast:94.101.224.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xec00

eth1:3    Link encap:Ethernet  HWaddr 00:21:91:f4:35:f9
          inet addr:94.101.224.187  Bcast:94.101.224.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xec00

eth1:4    Link encap:Ethernet  HWaddr 00:21:91:f4:35:f9
          inet addr:94.101.224.182  Bcast:94.101.224.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:114264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114264 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15773159 (15.7 MB)  TX bytes:15773159 (15.7 MB)


```dmesg |grep eth
```
[    1.038727] eth0: RTL8102e at 0xffffc9000063a000, 44:87:fc:59:44:d1, XID 04c00000 IRQ 25
[    1.041683] eth1: RTL8169sb/8110sb at 0xffffc9000064ec00, 00:21:91:f4:35:f9, XID 10000000 IRQ 18
[   16.729547] r8169: eth1: link up
[   27.493076] eth1: no IPv6 routers present
[ 3604.592504] r8169: eth1: link up
[ 3614.870006] eth1: no IPv6 routers present
[ 3643.230347] r8169: eth1: link up
[ 3654.060007] eth1: no IPv6 routers present

``` lspci -tv
```
           +-1c.0-[0000:01]----00.0  Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller
           +-1e.0-[0000:02]----01.0  D-Link System Inc DGE-528T Gigabit Ethernet Adapter

```ethtool eth1
```
Settings for eth1:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                             100baseT/Half 100baseT/Full
                                             1000baseT/Full
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes

```

---

### Post by uncaspi on 2010-11-17
It could be the firewall settings in your server.

---

### Post by siikaisz on 2010-11-17
that isnt problem

---

### Post by uncaspi on 2010-11-17
Check with route -n if you have the routes to host

---

### Post by siikaisz on 2010-11-17
route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
94.101.224.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         94.101.224.1    0.0.0.0         UG    100    0        0 eth1

```

---

### Post by siikaisz on 2010-11-17
colocation technician sayed what need all virtual interfaces make on loopback with mask 255.255.255.255 then all will work...

later will post results...

---

### Post by uncaspi on 2010-11-17
You have route only to eth1. This maybe a shot in the dark but are you able to issue sudo route add route0 gw x.x.x.x  eth1:0 and so on for the other 3.

---

### Post by siikaisz on 2010-11-17
PROBLEM SOLVED
new interafce configuration also routing from ISP...
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth1 lo:1 lo:2 lo:3 lo:4 lo:5 lo:6 lo:7 lo:8
iface lo inet loopback

# The primary network interface
iface eth1 inet static
 address 94.101.224.184
 netmask 255.255.255.0
 network 94.101.224.0
 broadcast 94.101.224.255
 gateway 94.101.224.1
 dns-nameservers 94.101.230.2
 dns-search heaven.lv

iface lo:1 inet static
 address 94.101.225.96
 netmask 255.255.255.255

iface lo:2 inet static
 address 94.101.225.97
 netmask 255.255.255.255

iface lo:3 inet static
 address 94.101.225.98
 netmask 255.255.255.255

iface lo:4 inet static
 address 94.101.225.99
 netmask 255.255.255.255

iface lo:5 inet static
 address 94.101.225.100
 netmask 255.255.255.255

iface lo:6 inet static
 address 94.101.225.101
 netmask 255.255.255.255

iface lo:7 inet static
 address 94.101.225.102
 netmask 255.255.255.255

iface lo:8 inet static
 address 94.101.225.103
 netmask 255.255.255.255

```

---


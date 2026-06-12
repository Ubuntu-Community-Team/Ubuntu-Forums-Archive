---
title: "Server with multiple eth connections, static connection can't connect to internet"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by gtr33m on 2009-11-09
Hi,

I've got a server running 9.04 server with gnome frontend installed.

The server has 3 ethernet connections. The main, eth0, is static, eth1 is DHCP assigned.  eth2 is not used at present.

This server is the DHCP and DNS server for the network.

The routing is handled by a separate Linksys router.

I have Virtualbox running on the server and the clients use eth1 bridged for their networking.  They each have a static IP assigned in their own setups and can connect to the internet just fine.

eth0 can ping and connect to any machine on the local network, but for some reason won't connect to the internet.  If I change it to DHCP it will work just fine, but I really need it to be static and would prefer it to be manually set rather than using a DHCP lease, especially since it's the DHCP server.

/etc/resolv.conf
```
domain medxxx.com.au
search medxxx.com.au
nameserver 192.168.2.4
nameserver 192.168.2.2
nameserver 192.168.2.1

```

/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The intel network interface

auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
        address 192.168.2.2
        netmask 255.255.255.0
        network 192.168.2.0
        gateway 192.168.2.1
        broadcast 192.168.2.255

# The primary broadcom network interface
auto eth1
iface eth1 inet dhcp
#        address 192.168.2.3
#        netmask 255.255.255.0
#        network 192.168.2.0
#        gateway 192.168.2.1
#        broadcast 192.168.2.255

# The secondary broadcom network interface
auto eth2
iface eth2 inet static
        address 192.168.5.2
        netmask 255.255.255.0
        network 192.168.5.0
#	gateway 192.168.2.1
	broadcast 192.168.5.255

```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:6d:fe:32  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe6d:fe32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1359351 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1399510 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:126965940 (126.9 MB)  TX bytes:121878239 (121.8 MB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:0f:1f:6d:fe:33  
          inet addr:192.168.2.155  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe6d:fe33/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1443704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:812876 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:565866523 (565.8 MB)  TX bytes:173435134 (173.4 MB)
          Interrupt:7 

eth2      Link encap:Ethernet  HWaddr 00:0e:0c:58:36:e4  
          inet addr:192.168.5.2  Bcast:192.168.5.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:408589 errors:0 dropped:0 overruns:0 frame:0
          TX packets:408589 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:177478197 (177.4 MB)  TX bytes:177478197 (177.4 MB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

virbr0    Link encap:Ethernet  HWaddr 9a:d6:d7:96:de:68  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::98d6:d7ff:fe96:de68/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3334 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:845243 (845.2 KB)

```

I'm a bit stumped as to what is causing it.  I thought maybe syntax, but I can't see it, and it still connects locally.

Anyone have any ideas?

---

### Post by Iowan on 2009-11-09
[QUOTE=gtr33m;8282644]The Linksys has the 192.168.2.1 address? What is in routing table (**route**)? Can the machine ping internet via IP address?

---

### Post by gtr33m on 2009-11-09
192.168.2.1 is the router.

Every other machine on the network uses it without issues and the only static routes set up on the linksys are for a vpn tunnel, and only a few port forwards for different virtual servers.

Pinging a local computer from the server works, but pinging an internet address resolves the ip address, but won't ping.

route:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.5.0     *               255.255.255.0   U     0      0        0 eth2
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
192.168.2.0     *               255.255.255.0   U     0      0        0 eth1
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0
default         mail.medxxxx.c 0.0.0.0         UG    100    0        0 eth1
default         mail.medxxxx.c 0.0.0.0         UG    100    0        0 eth0

```

192.168.5.0 is a subnet that I was planning to use to directly link 2 servers over their spare gigabit connections.

Thanks,

Mark

---


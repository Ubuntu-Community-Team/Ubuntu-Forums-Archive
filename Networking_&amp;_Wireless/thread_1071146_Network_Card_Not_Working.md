---
title: "Network Card Not Working"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by TigerWolf on 2009-02-15
I just got a new Gigabit network card for my linux box and it doesnt seem to be working. It wont get an IP at all.

It works if I set it as a static IP but not if I do dhcp.

Here is some details

```
root@polyserver:/home/tigerwolf/Desktop/r8169-6.009.00# lshw -C network
PCI (sysfs)  
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: eth0
       version: 10
       serial: 00:02:44:0d:02:e1
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.103 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: eth1
       version: 10
       serial: 00:e0:4c:50:18:a9
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=6.009.00-NAPI duplex=full firmware=N/A latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=1GB/s
root@polyserver:/home/tigerwolf/Desktop/r8169-6.009.00# 
root@polyserver:/home/tigerwolf/Desktop/r8169-6.009.00# dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:e0:4c:50:18:a9
Sending on   LPF/eth1/00:e0:4c:50:18:a9
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10

```

Setting static IP
```
root@polyserver:/home/tigerwolf/Desktop/r8169-6.009.00# ifconfig eth1 192.168.1.109

root@polyserver:/home/tigerwolf/Desktop/r8169-6.009.00# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:02:44:0d:02:e1  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:44ff:fe0d:2e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5490418 (5.2 MB)  TX bytes:1924614 (1.8 MB)
          Interrupt:5 Base address:0xe400 

eth1      Link encap:Ethernet  HWaddr 00:e0:4c:50:18:a9  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe50:18a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:168 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0x2000 


root@polyserver:/home/tigerwolf/Desktop/r8169-6.009.00# ping -I eth1 192.168.1.100
PING 192.168.1.100 (192.168.1.100) from 192.168.1.109 eth1: 56(84) bytes of data.
From 192.168.1.109 icmp_seq=2 Destination Host Unreachable
From 192.168.1.109 icmp_seq=3 Destination Host Unreachable
From 192.168.1.109 icmp_seq=4 Destination Host Unreachable
From 192.168.1.109 icmp_seq=6 Destination Host Unreachable
From 192.168.1.109 icmp_seq=7 Destination Host Unreachable
From 192.168.1.109 icmp_seq=8 Destination Host Unreachable


```


I can access the box from 192.168.1.100 and see the apache page... 

I installed the latest driver from realtek

Any ideas or suggestions?

---

### Post by nixscripter on 2009-02-17
It looks like it doesn't work either way. CHeck to make sure the connection is set up right with this command:

```
sudo ethtool eth1
```

It should say "link detected: yes" and have a speed and MTU set.

---

### Post by TigerWolf on 2009-02-18
This is what I get:
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
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: pumbg
	Current message level: 0x00000033 (51)
	Link detected: yes

```

---

### Post by TigerWolf on 2009-02-18
This is interesting:

tigerwolf@polyserver:~$ sudo mii-tool eth1
  No MII transceiver present!.
tigerwolf@polyserver:~$ sudo mii-tool eth0
eth0: negotiated 100baseTx-FD, link ok

---

### Post by TigerWolf on 2009-02-18
Anyone have any ideas? Im becoming very frustrated by this and have no idea how to fix it.

---

### Post by nixscripter on 2009-02-18
The next thing to look at is thre routing table. Run this command: ```
route
``` to make sure it's trying to send packets down the right interface.

---

### Post by TigerWolf on 2009-02-18
This is what I get: eth0 is the one that works and eth1 is the one im trying to get to work

```
tigerwolf@polyserver:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```

I manually set the IP address of eth1 and it seems to work:

```
tigerwolf@polyserver:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:44:0d:02:e1  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:44ff:fe0d:2e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1326193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1517623 errors:0 dropped:0 overruns:6 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:582653602 (582.6 MB)  TX bytes:958962612 (958.9 MB)
          Interrupt:5 Base address:0xe400 

eth1      Link encap:Ethernet  HWaddr 00:e0:4c:50:18:a9  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe50:18a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:620722501 overruns:0 frame:0
          TX packets:2 errors:0 dropped:5428 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:168 (168.0 B)
          Interrupt:10 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:75898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75898 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11299351 (11.2 MB)  TX bytes:11299351 (11.2 MB)


tigerwolf@polyserver:~$ ping -I 192.168.1.109 google.com
PING google.com (74.125.45.100) from 192.168.1.109 : 56(84) bytes of data.
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=1 ttl=244 time=454 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=2 ttl=244 time=463 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=3 ttl=244 time=447 ms


```


Its still not working if I do DHCLIENT though! What is wrong?

Could this be related? 

[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/326891](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/326891)

What can I do with this information?

---

### Post by nixscripter on 2009-02-22
Rather odd bug, but I don't think that's it.

Looking at the routing table, it looks like most of the traffic is going out eth0 anyway. See the two entries for 192.168.1.0? Try removing one of them:

```
sudo route del -net 192.168.97.1.0  eth0
```

This should make eth0 stop working for the moment and eth1 start. If it doesn't, you can reboot and then we can take a second look at that bug.

---


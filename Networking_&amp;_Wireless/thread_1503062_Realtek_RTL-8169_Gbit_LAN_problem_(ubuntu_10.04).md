---
title: "Realtek RTL-8169 Gbit LAN problem (ubuntu 10.04)"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by sauroman on 2010-06-06
Hi all,

I am having problems trying to get my LAN connecting to my router using Ubuntu 10.04.  Previous versions of Ubuntu has had no problems with this card.

I did manage to get it working for a few days with 10.04 until the kernel update last week which stopped it working.  I have since re-installed and using 10.04 before any updates again.  The NIC works fine on win 7 (duel boot) and have checked the power on lan setting in win 7 which is enabled by default.

I have been reading many forums over the last few days regarding this NIC to find a solution with no joy.  Does anyone know if the default r8169 driver has any problems?

I have tried connecting with a static and dynamic ip addresses (setting up the router accordingly for each method), disabling the NetworkManager and connecting manually.

My current status is, I am unable to receive a ip address from my router but with the NIC receiving no data this is not surprising.  It seems to be able to transmit. Other devices connecting to the router using dhcp connects ok.  NetworkManager also fails if attempt to connect through this.

My current details:

$ uname -r 
2.6.32-21-generic

$ ifconfig eth0 
```
eth0      Link encap:Ethernet  HWaddr 00:e0:4c:e1:2e:bb  
          inet6 addr: fe80::2e0:4cff:fee1:2ebb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6966 (6.9 KB)
          Interrupt:21 Base address:0xe000 

```

$ sudo ethtool eth0
```
Settings for eth0:
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
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
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

$ lshw -C network
```
*-network               
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:e0:4c:e1:2e:bb
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:21 ioport:de00(size=256) memory:fdfff000-fdfff0ff memory:fde00000-fde1ffff(prefetchable)

```

$ sudo dhclient eth0
```
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:e0:4c:e1:2e:bb
Sending on   LPF/eth0/00:e0:4c:e1:2e:bb
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.

```

If anything is else is required, please let me know and I will post.

Thanks!!
Darren

---

### Post by TRAyres on 2010-07-15
I have the same problem.

---

### Post by jMon54 on 2010-07-16
I posted earlier before stumbling across this.  Looks like it's the same problem for me with an new nic I just added to replace my failing on-board nic.

---

### Post by bkratz on 2010-07-16
It looks sorta familiar, see if this thread helps ( just saw it this morning), especially after post 8.

[http://ubuntuforums.org/showthread.php?t=1530977](http://ubuntuforums.org/showthread.php?t=1530977)

---


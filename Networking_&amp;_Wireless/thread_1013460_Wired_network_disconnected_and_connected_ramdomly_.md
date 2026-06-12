---
title: "Wired network disconnected and connected ramdomly when load package"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by entaneer on 2008-12-16
I didn't solve is the networking card problem.
I can connect to the internet and local network via dhcp. 
There no problem when only open webpage
But if I load file or package and update system. Network is disconnected and reconnect frequency.
disconnected ..... connnected
disconnected ..... connnected
disconnected ..... connnected
disconnected ..... connnected
disconnected ..... connnected

Same problem both ubuntu and kubuntu. static ip is get same problem too.
below are information for you.

Thanks for your help

**Hardware**
```
Laptop Acer Aspire 5542
Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
```

**OS**
```

Kubuntu (or Ubuntu) 8.10
Kernel 2.6.27-10-generic
```

**Kernel Log**
```

2008-12-17 08:48:48	b44	eth0: Link is up at 100 Mbps, full duplex.
2008-12-17 08:48:48	b44	eth0: Flow control is off for TX and off for RX.
2008-12-17 08:48:48		ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
2008-12-17 08:48:58	eth0	no IPv6 routers present
2008-12-17 08:51:38	b44	eth0: powering down PHY
2008-12-17 08:51:38	b44	eth0: Link is down.
2008-12-17 08:51:41	b44	eth0: Link is up at 100 Mbps, full duplex.
2008-12-17 08:51:41	b44	eth0: Flow control is off for TX and off for RX.
2008-12-17 08:51:41	b44	eth0: Flow control is off for TX and off for RX.
2008-12-17 09:26:09	b44	eth0: powering down PHY
2008-12-17 09:26:10	b44	eth0: Link is down.
2008-12-17 09:26:13	b44	eth0: Link is up at 100 Mbps, full duplex.
2008-12-17 09:26:13	b44	eth0: Flow control is off for TX and off for RX.
2008-12-17 09:26:13	b44	eth0: Flow control is off for TX and off for RX.
2008-12-17 09:26:22	b44	eth0: powering down PHY
2008-12-17 09:26:23	b44	eth0: Link is down.
2008-12-17 09:26:23	b44	eth0: Link is down.
2008-12-17 09:26:26	b44	eth0: Link is up at 100 Mbps, full duplex.
2008-12-17 09:26:26	b44	eth0: Flow control is off for TX and off for RX.

```

**System Log**
```

2008-12-17 09:26:15	nott-laptop	NetworkManager	<info>  DHCP: device eth0 state changed preinit -> bound 
2008-12-17 09:26:15	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
2008-12-17 09:26:15	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
2008-12-17 09:26:15	nott-laptop	NetworkManager	<info>    address 10.2.15.191 
2008-12-17 09:26:15	nott-laptop	NetworkManager	<info>    prefix 24 (255.255.255.0) 
2008-12-17 09:26:15	nott-laptop	NetworkManager	<info>    gateway 10.2.15.254 
2008-12-17 09:26:15	nott-laptop	NetworkManager	<info>    nameserver '192.168.1.3' 
2008-12-17 09:26:15	nott-laptop	NetworkManager	<info>    nameserver '202.28.18.65' 
2008-12-17 09:26:15	nott-laptop	NetworkManager	<info>    nameserver '203.146.237.237' 
2008-12-17 09:26:15	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
2008-12-17 09:26:15	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
2008-12-17 09:26:15	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
2008-12-17 09:26:15	nott-laptop	avahi-daemon[4794]	Joining mDNS multicast group on interface eth0.IPv4 with address 10.2.15.191.
2008-12-17 09:26:15	nott-laptop	avahi-daemon[4794]	New relevant interface eth0.IPv4 for mDNS.
2008-12-17 09:26:15	nott-laptop	avahi-daemon[4794]	Registering new address record for 10.2.15.191 on eth0.IPv4.
2008-12-17 09:26:15	nott-laptop	dhclient	bound to 10.2.15.191 -- renewal in 36196 seconds.
2008-12-17 09:26:16	nott-laptop	NetworkManager	<info>  (eth0): device state change: 7 -> 8 
2008-12-17 09:26:16	nott-laptop	NetworkManager	<info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
2008-12-17 09:26:16	nott-laptop	NetworkManager	<info>  Activation (eth0) successful, device activated. 
2008-12-17 09:26:16	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
2008-12-17 09:26:20	nott-laptop	ntpdate[11317]	no server suitable for synchronization found
2008-12-17 09:26:22	nott-laptop	kernel	[ 3580.627539] b44: eth0: powering down PHY
2008-12-17 09:26:22	nott-laptop	kernel	[ 3580.988213] b44: eth0: Link is down.
2008-12-17 09:26:22	nott-laptop	NetworkManager	<info>  (eth0): carrier now OFF (device state 8) 
2008-12-17 09:26:22	nott-laptop	NetworkManager	<info>  (eth0): device state change: 8 -> 2 
2008-12-17 09:26:22	nott-laptop	NetworkManager	<info>  (eth0): deactivating device (reason: 0). 
2008-12-17 09:26:22	nott-laptop	NetworkManager	<info>  eth0: canceled DHCP transaction, dhcp client pid 11252 
2008-12-17 09:26:22	nott-laptop	NetworkManager	<WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess  
2008-12-17 09:26:22	nott-laptop	avahi-daemon[4794]	Withdrawing address record for 10.2.15.191 on eth0.
2008-12-17 09:26:22	nott-laptop	avahi-daemon[4794]	Leaving mDNS multicast group on interface eth0.IPv4 with address 10.2.15.191.
2008-12-17 09:26:22	nott-laptop	avahi-daemon[4794]	Interface eth0.IPv4 no longer relevant for mDNS.
2008-12-17 09:26:25	nott-laptop	kernel	[ 3583.989577] b44: eth0: Link is up at 100 Mbps, full duplex.
2008-12-17 09:26:25	nott-laptop	kernel	[ 3583.989588] b44: eth0: Flow control is off for TX and off for RX.
2008-12-17 09:26:25	nott-laptop	NetworkManager	<info>  (eth0): carrier now ON (device state 2) 
2008-12-17 09:26:25	nott-laptop	NetworkManager	<info>  (eth0): device state change: 2 -> 3 
2008-12-17 09:26:25	nott-laptop	NetworkManager	<info>  Activation (eth0) starting connection 'Auto eth0' 
2008-12-17 09:26:25	nott-laptop	NetworkManager	<info>  (eth0): device state change: 3 -> 4 
2008-12-17 09:26:25	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
2008-12-17 09:26:25	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
2008-12-17 09:26:25	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
2008-12-17 09:26:25	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
2008-12-17 09:26:25	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
2008-12-17 09:26:25	nott-laptop	NetworkManager	<info>  (eth0): device state change: 4 -> 5 
2008-12-17 09:26:25	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
2008-12-17 09:26:25	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
2008-12-17 09:26:25	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
2008-12-17 09:26:25	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
2008-12-17 09:26:25	nott-laptop	NetworkManager	<info>  (eth0): device state change: 5 -> 7 
2008-12-17 09:26:25	nott-laptop	NetworkManager	<info>  Activation (eth0) Beginning DHCP transaction. 
2008-12-17 09:26:25	nott-laptop	NetworkManager	<info>  dhclient started with pid 11338 
2008-12-17 09:26:25	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
2008-12-17 09:26:25	nott-laptop	dhclient	Internet Systems Consortium DHCP Client V3.1.1
2008-12-17 09:26:25	nott-laptop	dhclient	Copyright 2004-2008 Internet Systems Consortium.
2008-12-17 09:26:25	nott-laptop	dhclient	All rights reserved.
2008-12-17 09:26:25	nott-laptop	dhclient	For info, please visit http://www.isc.org/sw/dhcp/
2008-12-17 09:26:25	nott-laptop	dhclient	
2008-12-17 09:26:25	nott-laptop	dhclient	wmaster0: unknown hardware address type 801
2008-12-17 09:26:25	nott-laptop	NetworkManager	<info>  DHCP: device eth0 state changed normal exit -> preinit 
2008-12-17 09:26:25	nott-laptop	dhclient	wmaster0: unknown hardware address type 801
2008-12-17 09:26:25	nott-laptop	dhclient	Listening on LPF/eth0/00:0a:e4:f8:c4:55
2008-12-17 09:26:25	nott-laptop	dhclient	Sending on   LPF/eth0/00:0a:e4:f8:c4:55
2008-12-17 09:26:25	nott-laptop	dhclient	Sending on   Socket/fallback
2008-12-17 09:26:28	nott-laptop	dhclient	DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
2008-12-17 09:26:28	nott-laptop	dhclient	DHCPOFFER of 10.2.15.191 from 10.2.15.254
2008-12-17 09:26:28	nott-laptop	dhclient	DHCPREQUEST of 10.2.15.191 on eth0 to 255.255.255.255 port 67
2008-12-17 09:26:28	nott-laptop	dhclient	DHCPACK of 10.2.15.191 from 10.2.15.254
2008-12-17 09:26:28	nott-laptop	NetworkManager	<info>  DHCP: device eth0 state changed preinit -> bound 
2008-12-17 09:26:28	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
2008-12-17 09:26:28	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
2008-12-17 09:26:28	nott-laptop	NetworkManager	<info>    address 10.2.15.191 
2008-12-17 09:26:28	nott-laptop	NetworkManager	<info>    prefix 24 (255.255.255.0) 
2008-12-17 09:26:28	nott-laptop	NetworkManager	<info>    gateway 10.2.15.254 
2008-12-17 09:26:28	nott-laptop	NetworkManager	<info>    nameserver '192.168.1.3' 
2008-12-17 09:26:28	nott-laptop	NetworkManager	<info>    nameserver '202.28.18.65' 
2008-12-17 09:26:28	nott-laptop	NetworkManager	<info>    nameserver '203.146.237.237' 
2008-12-17 09:26:28	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
2008-12-17 09:26:28	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
2008-12-17 09:26:28	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
2008-12-17 09:26:28	nott-laptop	avahi-daemon[4794]	Joining mDNS multicast group on interface eth0.IPv4 with address 10.2.15.191.
2008-12-17 09:26:28	nott-laptop	avahi-daemon[4794]	New relevant interface eth0.IPv4 for mDNS.
2008-12-17 09:26:28	nott-laptop	avahi-daemon[4794]	Registering new address record for 10.2.15.191 on eth0.IPv4.
2008-12-17 09:26:28	nott-laptop	dhclient	bound to 10.2.15.191 -- renewal in 36080 seconds.
2008-12-17 09:26:29	nott-laptop	NetworkManager	<info>  (eth0): device state change: 7 -> 8 
2008-12-17 09:26:29	nott-laptop	NetworkManager	<info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
2008-12-17 09:26:29	nott-laptop	NetworkManager	<info>  Activation (eth0) successful, device activated. 
2008-12-17 09:26:29	nott-laptop	NetworkManager	<info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 

```

**ifconfig**
```

eth0      Link encap:Ethernet  HWaddr 00:0a:e4:f8:c4:55
          inet addr:10.2.15.191  Bcast:10.2.15.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fef8:c455/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47253 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23606 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:41736894 (41.7 MB)  TX bytes:2240930 (2.2 MB)
          Interrupt:23

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:16124 (16.1 KB)  TX bytes:16124 (16.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:0e:0f:36
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-0E-0F-36-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

**route -n**
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.2.15.0       0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.2.15.254     0.0.0.0         UG    0      0        0 eth0

```

**cat /etc/resolv.conf**
```

# Generated by NetworkManager
nameserver 192.168.1.3
nameserver 202.28.18.65
nameserver 203.146.237.237

```

**cat /etc/hosts**
```

127.0.0.1       localhost
127.0.1.1       nott-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by entaneer on 2008-12-17
OK
I founded it.
This is Kernel and compiz BUG :(

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/279102](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/279102)

---

### Post by Godspell on 2010-01-13
I'm also using the same laptop but with Ubuntu 9.1 x64.
Everything works well for me...didn't have to install any driver at all. For the ATI GPU, I switched to proprietary driver and it works just fine.
If you haven't gone far with the OS, why not change it to karmic? at least 32bit???
Sorry it's such a lame idea, I'm still a noob in Linux.

Cheers.
GS

---


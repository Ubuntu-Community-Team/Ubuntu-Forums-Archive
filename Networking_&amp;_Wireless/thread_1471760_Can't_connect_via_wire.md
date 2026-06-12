---
title: "Can't connect via wire"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by dracojames on 2010-05-03
[http://ubuntuforums.org/showthread.php?t=1468900]("http://ubuntuforums.org/showthread.php?t=1468900")
Hey, I'm having a very similar problem; just did a fresh install of 10.04 (32-bit) on an Acer laptop. My wired connection won't connect.

When I plug in the ethernet cable, the 'Auto eth0' connection shows up, attempts to connect, then fails. If I check the connections, it says I'm disconnected, but Auto eth0 is available (any further attempts to connect fail as well).

**ifconfig -a** produces the following
```
~>ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:d3:41:38:46  
          inet6 addr: fe80::216:d3ff:fe41:3846/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:240 (240.0 B)  TX bytes:19784 (19.7 KB)
          Interrupt:23 Base address:0x2000 

eth0:avahi Link encap:Ethernet  HWaddr 00:16:d3:41:38:46  
          inet addr:169.254.5.190  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:ce:78:fb:c4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I've no idea why eth0 seems to be assigned an IPv6 address, nor what the "eth0:avahi" section is doing there. The 169.254... IP that's showing up makes no sense (the network I'm on uses 192.168.2.xxx format) and that isn't the external IP for the network, either.

The **dhclient eth0** command failed much in the same way as it did for Hunnter

**lshw -C network**'s output is below; 

```
~>sudo lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0200000-c0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:41:38:46
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:23 ioport:a000(size=256) memory:c0202000-c02020ff memory:44000000-4401ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:ce:78:fb:c4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```

Any help would be greatly appreciated

---

### Post by dracojames on 2010-05-03
Well, I've now managed to get internet working on the laptop (wireless internet, that is). I connected the computer running 10.04 to a Windows 7 laptop via ethernet cable, and enabled Internet Connection Sharing on the Win7 machine.

This allowed me to access the internet on the 10.04 laptop so I could download the wireless drivers I needed, which installed and (after a restart) are working perfectly. However, while it's no longer a top priority, it would be nice to be able to connect to wired networks should I find myself needing to do so at some point.

---

### Post by Iowan on 2010-05-03
Posts moved to new thread.

---


---
title: "Ethernet on win98 and 9.04"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by joeyknuccione on 2009-09-02
Problem: Ethernet works on win98, no longer on U9.04.

I recently could reinstall the 3Com driver on win98, restart, and then U9.04 would see my ethernet. Now it no longer works even this way.

Some info:
```

From Network Tools:

eth0 (I've also seen an "unrecognized pan0", see below)

IPv6 IP=fe80::260:8ff:fe3f:e6b Netmask=64 Scope=Link

IPv4 IP=192.168.254.1    Netmask=255.255.255.0

Interface Info:

Hardware address: 00:60:08:3f:0e:6b
----------------------------------

Active Network Connections

Wired connection 1 (default)

Interface: Ethernet (eth0)

Hardware Address: 00:60:08:3F:0E:6B

Driver: 3c59x (3Com ethernet adapter)

Speed: 10 Mb/s 
Security: None

IP Address: ***.***.***.*

Broadcast Address: 192.168.254.255

Subnet Mask: 255.255.255.0

Default Route: 192.168.254.254

Primary DNS: 192.168.254.254

LSPCI:

01:08.0 Ethernet controller: 3Com Corporation 3c900 10Mbps Combo [Boomerang]
-------------------------------
Command: sudo lshw -C network

Returns:

 *-network               

       description: Ethernet interface

       product: 3c900 10Mbps Combo [Boomerang]

       vendor: 3Com Corporation

       physical id: 8

       bus info: pci@0000:01:08.0

       logical namsue: eth0

       version: 00

       serial: 00:60:08:3f:0e:6b

       size: 10MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=off broadcast=yes driver=3c59x duplex=half latency=64 link=no maxlatency=8 mingnt=3 module=3c59x multicast=yes port=MII speed=10MB/s

  *-network DISABLED

       description: Ethernet interface

       physical id: 1

       logical name: pan0

       serial: 62:27:d9:c0:e3:26

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
---------------------------
Command: sudo lsmod

Returns:

>>>This was when functioning

 *-network DISABLED

       description: Ethernet interface

       physical id: 1

       logical name: pan0

       serial: ce:52:c3:4b:ee:69

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
Please help, and thanks in advance for even reading or trying.

---

### Post by Iowan on 2009-09-02
What you've shown seems kosher - what doesn't work? Can you ping gateway/router? **ifconfig -a** shows proper IP address?

---

### Post by joeyknuccione on 2009-09-21
Sorry for delay, work and all...

ifconfig -a shows:

unable to resolve host joe-desktop

then it shows:

eth0      Link encap:Ethernet  HWaddr 00:60:08:3f:0e:6b  
          inet addr:***.***.***.*  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::260:8ff:fe3f:e6b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:93 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:50083 (50.0 KB)  TX bytes:9333 (9.3 KB)
          Interrupt:3 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr 86:24:b7:ba:b5:f3  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
---------------------------
That's while the network is functioning in U9.04.

Again, my issue is when I restart it won't come up unless I go into win98, reinstall drivers, shutdown, and restart U9.04.

---


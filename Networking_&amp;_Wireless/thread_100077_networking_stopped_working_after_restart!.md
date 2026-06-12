---
title: "networking stopped working after restart!"
date: 2005-12-06
forum: Networking &amp; Wireless
---

### Post by dionisis on 2005-12-06
Hello all,
I faced a very weird problem today and I would want your help on it. First of all I have Ubuntu 5.10 on, working nicely for quite a long time. I had internet access (through LAN) without any problems until tonight.

When I rebooted, the system could not find the network. On the same machine, with the same network card, it works fine with WinXP.

Here is some troubleshooting info:

First of all, it seems to be connected on the physical layer:
```

sudo mii-tool eth1
eth1: no autonegotiation, 10baseT-HD, link ok

```
The driver for the card seems to be loaded
```

lspci | grep Eth
0000:00:0b.0 Ethernet controller: 3Com Corporation 3c980-TX Fast Etherlink XL Server Adapter [Cyclone] (rev 24)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)

lsmod | grep mii
mii                     5248  2 via_rhine,3c59x

```

but I don't seem to get any IP Address.
```

ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:50:8D:6A:43:CF
          inet6 addr: fe80::250:8dff:fe6a:43cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2959 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:338412 (330.4 KiB)  TX bytes:2772 (2.7 KiB)
          Interrupt:23 Base address:0xed00

```

We use DHCP so I tried to run the dhcp client
```

sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:50:8d:6a:43:cf
Sending on   LPF/eth1/00:50:8d:6a:43:cf
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPNAK from 128.86.152.1
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

The routing tables are empty:
```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

Finally, in case someone finds this info related and useful:
```

cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
iface eth1 inet dhcp

iface eth0 inet dhcp

auto eth1

auto eth0

```

It looks like I get a response from the DHCP server, but then I don't get any IP offered. Any clues why this happens? I repeat that it works fine when I boot on XP (from where I write this post now).

Thanks in advance.

---

### Post by yaaarrrgg on 2005-12-08
i'm probably not much help, but had a similar error message with my wireless card (after a power failure).  i just unloaded my networking modules, then modprobed them back, and did a ifup.  my card is working again, but not sure you have the same problem.  that is all i know...

---

### Post by dionisis on 2005-12-08
Thanks for the reply. The problem seemed to be the DHCP server that was not working properly. After a restart of the DHCP server (and hours lost searching) everything works fine again! :)

---


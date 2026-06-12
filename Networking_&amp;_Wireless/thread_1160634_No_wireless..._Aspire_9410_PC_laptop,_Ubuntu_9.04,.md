---
title: "No wireless... Aspire 9410 PC laptop, Ubuntu 9.04, Intel PRO/Wireless 3945ABG"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by ctrain79 on 2009-05-15
Wireless not working.

I don't understand which interface is wireless out of those listed with the command ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:16:d3:58:28:4a  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe58:284a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12540 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20257965 (20.2 MB)  TX bytes:1658614 (1.6 MB)
          Interrupt:251 

eth1      Link encap:Ethernet  HWaddr 00:19:d2:c6:b4:9c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1:avahi Link encap:Ethernet  HWaddr 00:19:d2:c6:b4:9c  
          inet addr:169.254.9.236  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-C6-B4-9C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

From iwconfig, it looks like it is eth1.

Also, from kernel boot messages:

```
russell@russell-laptop:~$ dmesg | grep "eth1"
\[   15.409023\] udev: renamed network interface wlan0 to eth1
\[   21.729447\] ADDRCONF(NETDEV_UP): eth1: link is not ready
```

Network configuration gives:

```
russell@russell-laptop:~$  sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:16:d3:58:28:4a
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.103 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:c6:b4:9c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7e:50:68:1d:44:90
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Scanning for networks:

```
russell@russell-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth1      No scan results

pan0      Interface doesn't support scanning.

```

Architecture:

```
russell@russell-laptop:~$ uname -mr
2.6.28-11-generic i686

```

And, finally, restarting the network:

```
russell@russell-laptop:~$  sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                                           There is already a pid file /var/run/dhclient.eth0.pid with pid 2669
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:16:d3:58:28:4a
Sending on   LPF/eth0/00:16:d3:58:28:4a
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 4039
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth1/00:19:d2:c6:b4:9c
Sending on   LPF/eth1/00:19:d2:c6:b4:9c
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:16:d3:58:28:4a
Sending on   LPF/eth0/00:16:d3:58:28:4a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.0.103 from 192.168.0.1
DHCPREQUEST of 192.168.0.103 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.103 from 192.168.0.1
bound to 192.168.0.103 -- renewal in 232817 seconds.
 * if-up.d/mountnfs[eth0]: waiting for interface eth1 before doing NFS mounts
 * if-up.d/mountnfs[eth0]: waiting for interface eth2 before doing NFS mounts
 * if-up.d/mountnfs[eth0]: waiting for interface ath0 before doing NFS mounts
 * if-up.d/mountnfs[eth0]: waiting for interface wlan0 before doing NFS mounts
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth1/00:19:d2:c6:b4:9c
Sending on   LPF/eth1/00:19:d2:c6:b4:9c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * if-up.d/mountnfs[eth1]: waiting for interface eth2 before doing NFS mounts
 * if-up.d/mountnfs[eth1]: waiting for interface ath0 before doing NFS mounts
 * if-up.d/mountnfs[eth1]: waiting for interface wlan0 before doing NFS mounts
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up wlan0.

```

Every time I try to get wireless working, it just leads me on a wild goose chase, so I'm finally breaking down and asking for help on the forums.  Please help!

---

### Post by ctrain79 on 2009-05-15
It would be nice to figure this out while I have a nice cable connection at the moment.

Seriously, last time I tried to solve this issue, I spend days on it, literally... it's getting just a little bit frustrating, seeing as how earlier versions of Ubuntu worked fine.

---

### Post by chili555 on 2009-05-15
> I have a nice cable connection at the moment.Your wireless interface is eth1.

Network Manager, which is installed by default, will not allow a wireless connection if you have a wired connection, which you do:> eth0      Link encap:Ethernet  HWaddr 00:16:d3:58:28:4a  
          inet addr:192.168.0.103If you reboot with the wire detached, can you click the network icon, see your network and connect?

---


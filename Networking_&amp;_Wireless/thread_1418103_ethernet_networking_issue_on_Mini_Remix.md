---
title: "ethernet networking issue on Mini Remix"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by act.habbit.char.destiny on 2010-02-28
Hi Friends,

I am new to Ubuntu. I decided to install it on my eee pc 1005HA. Unfortunately, ubuntu  mini remix installed on the netbook has a peculiar problem. Whenever I suspend or hibernate the system and later start it, the system's ethernet capability totally disappears.

some output for typical commands are given below

```

ifconfig

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:780 (780.0 B)  TX bytes:780 (780.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:c8:dc:cb  
          inet6 addr: fe80::225:d3ff:fec8:dccb/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:244 (244.0 B)  TX bytes:4752 (4.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-25-D3-C8-DC-CB-63-38-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
______________________________________________________________
lshw -C network
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:25:d3:c8:dc:cb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
________________________________________________________________________
sudo dhclient eth0

Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device


```I tried changing the /etc/network/interfaces file to automatically detect the eth0 interface but it is making the system unresponsive.

Please help me..

Thanks for your time

---


---
title: "Can't recieve IP, Ping router, connect net"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by szarywilq on 2009-04-21
Hi all, 

First of all &#8211; it is not a new installation, I have Intrepid for month, and everything was just fine until yesterday.

I have 2 pc's (xp/ubuntu and xp only) and Toshiba notebook (xp/ubuntu) And net is working everywhere, on all systems, even on live cd, except Toshiba and ubuntu since yesterady


> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:33:55:2c:27  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:1476394408 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:219 Base address:0x4000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:33:55:2c:27  
          inet addr:169.254.2.247  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:219 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

wlan0     Link encap:Ethernet  HWaddr 00:21:5c:29:bd:a5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

wmaster0  Link encap:UNSPEC  HWaddr 00-21-5C-29-BD-A5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

> Ping router
mateusz@mateusz-laptop:~$ ping 192.168.1.1 
From 169.254.7.130 icmp_seq=4 Destination Host Unreachable 

> ROUTE
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
link-local      *               255.255.0.0     U     0      0        0 wlan0 
link-local      *               255.255.0.0     U     0      0        0 pan0 
link-local      *               255.255.0.0     U     0      0        0 eth0 
default         *               0.0.0.0         U     1000   0        0 wlan0 

> DHCLIENT
root@mateusz-laptop:/home/mateusz# dhclient 
There is already a pid file /var/run/dhclient.pid with pid 6090 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.1.1 
Copyright 2004-2008 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
Listening on LPF/pan0/d2:38:55:9f:6f:bc 
Sending on   LPF/pan0/d2:38:55:9f:6f:bc 
Listening on LPF/wlan0/00:21:5c:29:bd:a5 
Sending on   LPF/wlan0/00:21:5c:29:bd:a5 
Listening on LPF/wmaster0/ 
Sending on   LPF/wmaster0/ 
Listening on LPF/eth0/00:1e:33:55:2c:27 
Sending on   LPF/eth0/00:1e:33:55:2c:27 
Sending on   Socket/fallback 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9 
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 15 
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 11 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 18 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19 
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 93 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 


> INTERFACES
auto lo 
iface lo inet loopback 

Router also do not see toshiba on ubuntu on routing table.


It just stopped working.

Pls help!

---

### Post by Iowan on 2009-04-21
I s'pose you noticed that the machine got an avahi address (169.254.X.X)...
That seems to happen when DHCP fails. What are results of **lshw -C network**?

---

### Post by szarywilq on 2009-04-21
Firstly, I have also tried static connection. And again - works on every computer except ubuntu/toshiba. Almost same errors.
Once, I have also turned off avahi - after DHCP no offers it just did not recieved avahi IP.

>  *-generic                
       description: Ethernet interface 
       product: Illegal Vendor ID 
       vendor: Illegal Vendor ID 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: ff 
       serial: 00:1e:33:55:2c:27 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 66MHz 
       capabilities: bus_master vga_palette cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=255 link=yes maxlatency=255 mingnt=255 module=r8169 multicast=yes port=MII speed=100MB/s 
  *-network 
       description: Wireless interface 
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: wmaster0 
       version: 61 
       serial: 00:21:5c:29:bd:a5 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: f6:ae:26:6a:f7:79 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by Iowan on 2009-04-21
> *-generic
description: Ethernet interface
product: [COLOR="Red"]Illegal Vendor ID[/COLOR]
vendor: [COLOR="Red"]Illegal Vendor ID[/COLOR]
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: ff
serial: 00:1e:33:55:2c:27
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock: 66MHz
capabilities: bus_master vga_palette cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=255 link=yes maxlatency=255 mingnt=255 module=r8169 multicast=yes port=MII speed=100MB/s
*-network Curious - I looked up your [MAC address]("http://www.coffer.com/mac_find/") and could not discover the vendor, either.  What kind is it?

---

### Post by szarywilq on 2009-04-21
used same page and it showed me [http://www.inventec.com/](http://www.inventec.com/) ;]

---

### Post by Iowan on 2009-04-21
OK, so did I this time - I must have pasted in an extra space the first time. What driver is it supposed to be using? Something has **lshw** confused...

---

### Post by szarywilq on 2009-04-22
I hope you ask abaout this:
> 
sudo lspci -v:
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. TRL8101E/RTL8102E PCI Express Fast Ethernet controller (rev ff) (prog-if ff)
!!! Unknown header type 7f
Kernel driver in use: r8169
Kernel modules: r8169

03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
Subsystem: Intel Corparation Device 1101
Flags: bus master, fast devsel, latency 0, IRQ 218
Memory at d4200000 (64-bit, non-prefetchable) [size=8k]
Capabilities: [c8] Power Managnement version 3
Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0
Enable+
Capabilities: [e0] Express Endpoint, MSI 00
Capabilities: [100] Advenced Error Reporting <?>
Capabilities: [140] Device Serial Number a5-bd-29-ff-ff-5c-21-00
Kernel driver in use: iwlagn
Kernel modules: iwlagn 

---


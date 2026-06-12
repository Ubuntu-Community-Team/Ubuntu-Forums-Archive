---
title: "Ultimate Noob Seeks wireless help xps studio 13"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by j0hnZ on 2009-05-02
Ok so here is basically my problem, I can't reliably use wireless at all.  I have vista 64 bit and ubuntu 9.04 64 bit running in dual boot.  I run Vista and wireless works flawlessly.  I jump over the Jaunty and wireless either fails to connect via WPA2 encryption or doesn't do anything.

I'm not very familiar with command line and I have already tried a few things such as installed this package linux-backports-moduls -jaunty and that pretty much did nothing for me.

I performed another command to see what wireless card I had and this is what it showed me:

06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Atheros Communications Inc. Device 0200
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at f0400000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k

It is the Dell Wireless 1510 802.11n Mini card if that helps anything.

Here is my ifconfig if it will help:

eth0      Link encap:Ethernet  HWaddr 00:22:19:e1:44:d1  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:19ff:fee1:44d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13532 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10813 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11015517 (11.0 MB)  TX bytes:1902726 (1.9 MB)
          Interrupt:19 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2047 (2.0 KB)  TX bytes:2047 (2.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:5f:62:49:41  
          inet6 addr: fe80::222:5fff:fe62:4941/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2684 (2.6 KB)  TX bytes:7360 (7.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-5F-62-49-41-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by j0hnZ on 2009-05-02
I was looking in some other thread and it looked like people wanted to see what this other command said so here is what that one said:

sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:22:19:e1:44:d1
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.103 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:5f:62:49:41
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ba:f9:af:59:86:1d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by j0hnZ on 2009-05-02
Ok well I turned off WPA encryption and wireless works.  So I guess WPA is broken.

---


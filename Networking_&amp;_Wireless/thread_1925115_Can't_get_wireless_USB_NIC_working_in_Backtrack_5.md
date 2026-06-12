---
title: "Can't get wireless USB NIC working in Backtrack 5"
date: 2012-02-14
forum: Networking &amp; Wireless
---

### Post by sneddy on 2012-02-14
*not sure if this is the correct prefix*
I'm pretty new to Linux (as might be obvious!), and I've spent hours this morning googling everything I could to try and fix this on my own. I'm starting a course in digital forensics in a couple of weeks, and I'll need to use Backtrack for tutorials/labs, so I'm trying to get a headstart and install it now. I know it has a really high learning curve, but I don't really have a choice where to start! The install went fine, but I've no idea how to get my Belkin USB Wireless NIC working. 

This is what I have so far:

> root@bt:/# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:d0:47:c1  
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fed0:47c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:237 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45943 (45.9 KB)  TX bytes:3982 (3.9 KB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:81 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11177 (11.1 KB)  TX bytes:11177 (11.1 KB)

[B]wlan0     Link encap:Ethernet  HWaddr 00:1c:df:db:d1:e6  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/B]

wlan1     Link encap:Ethernet  HWaddr 00:0d:0b:77:1f:23  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@bt:/# ifconfig wlan0 up
SIOCSIFFLAGS: No such file or directory
root@bt:/# 

root@bt:/# lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 005: ID 050d:705c Belkin Components 802.11bg**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

root@bt:/# lshw -C network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:d0:47:c1
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5705-v3.16 ip=192.168.1.13 latency=32 link=yes mingnt=64 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:11 memory:faff0000-faffffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32 maxlatency=34 mingnt=2
       resources: memory:fafef000-fafeffff
  *-network DISABLED
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wlan1
       version: 01
       serial: 00:0d:0b:77:1f:23
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38 firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11abg
       resources: irq:11 memory:5c000000-5c00ffff
[B]  *-network DISABLED
       description: Wireless interface
       physical id: 2
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:1c:df:db:d1:e6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=zd1211rw driverversion=2.6.38 firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg[/B]
 

wlan0 is the old onboard card (very old!) and the Atheros is an old PCMCIA card. The one I'm trying to get online is wlan0. According to someone on this forum, the F5D7050 usually works straight outta the box, but no luck for me. It uses either

Chip 1: Ralink RT2571W
or
Chip 2: Ralink RT2528

according to this page:
[http://wikidevi.com/wiki/Belkin_F5D7050_v3](http://wikidevi.com/wiki/Belkin_F5D7050_v3)

and I think the linux driver for it would be rt73usb?

EDIT: Also tried to get the Atheros PCMCIA card working. Used 'ifconfig wlan1 up' to get it up, but when I try 'dhclient wlan1' it only gets to dhcp discover, never an offer. The card is a/b/g, so I tried my router on various settings (b/g/n only, b only, g only, etc) but none of them made any difference. 

Anyway, if anyone can help it would be really appreciated!

---


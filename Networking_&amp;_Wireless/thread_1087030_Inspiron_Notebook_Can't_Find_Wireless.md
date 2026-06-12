---
title: "Inspiron Notebook Can't Find Wireless"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by Nikorasu on 2009-03-04
Hey everyone,

Sorry, as I know this is a fairly common problem, but I can't find any solutions online specific to my circumstances.

My apartment uses a WEP wireless network, and although my laptop (Inspiron E1505) can find and connect to it just fine in Windows (I use a dual boot), it cannot find it, much less connect to it, in Ubuntu 8.1.  I'm currently connected using a hard cable, and since I've done that the wireless light on my keyboard has shut off, although it was still lit before that, and I couldn't see any wireless networks then either.

lshw reads:

```
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:6f:b4:88
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.5 latency=64 module=ssb multicast=yes
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1b:fc:44:09:3b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 86:84:f3:5c:93:61
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```
iwconfig reads:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

I don't know if this a driver issue or what...thanks in advance for your help and sorry again to have a repetitive question.

---


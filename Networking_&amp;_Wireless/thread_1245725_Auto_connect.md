---
title: "Auto connect"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by andycastille on 2009-08-20
I have an internal wireless Internet adapter and and extension card. When I connect the extension card to a wireless network, the internal adapter connects to the same network and it slows down my connection speed for both. How can I disable the internal adapter?:confused:

---

### Post by Iowan on 2009-08-21
You've checked BIOS? Another option (somewhat crude) is to set up the internal for a manual address - not static - via */etc/network/interfaces*.

---

### Post by andycastille on 2009-08-21
How do i change that? What do I change it to?

---

### Post by Iowan on 2009-08-22
Post results of **ifconfig -a**. It occurs to me that Network Manager usually controls only one interface at a time, so I'm curious how both got activated.  What is in */etc/network/interfaces*? The "crude" method would change a line similar to ```
iface wlan0 inet dhcp
``` to ```
iface wlan0 inet manual
```

---

### Post by andycastille on 2009-08-22
[B]etc/network/interfaces: auto lo
                                      iface lo inet loopback
[/B]

---

### Post by andycastille on 2009-08-23
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:02:2d:5c:16:28  
          inet6 addr: fe80::202:2dff:fe5c:1628/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1732 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1565 errors:606 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1599150 (1.5 MB)  TX bytes:648759 (648.7 KB)
          Interrupt:11 Base address:0xe100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30128 (30.1 KB)  TX bytes:30128 (30.1 KB)

pan0      Link encap:Ethernet  HWaddr da:e5:c7:a0:b5:28  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:f0:ee:59:a6  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:f0ff:feee:59a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1385 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1863779 (1.8 MB)  TX bytes:230025 (230.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-F0-EE-59-A6-39-61-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Iowan on 2009-08-24
:confused: What is the extension card? 
Perhaps you could post results of **lshw -C network**.

---

### Post by andycastille on 2009-08-26
D-Link System Atheros AR5001X+ Wireless Network Adapter

I can't get the command to work. I typed the exact text from the  network panel drop down menu.

---

### Post by andycastille on 2009-08-27
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1c:f0:ee:59:a6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.2.5 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: eth0
       serial: 00:02:2d:5c:16:28
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.10 multicast=yes wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 86:7e:a1:b2:e6:14
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---


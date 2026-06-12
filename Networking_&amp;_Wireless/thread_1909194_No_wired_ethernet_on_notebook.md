---
title: "No wired ethernet on notebook"
date: 2012-01-14
forum: Networking &amp; Wireless
---

### Post by jchiso on 2012-01-14
[LIST]Acer Aspire 5253 notebook[/LIST]
[LIST]Running Maverick[/LIST]
[LIST]The device works with Windows 7[/LIST]
[LIST]Wireless networking works fine in Ubuntu[/LIST]
**sudo lshw -c network**

```
*-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:06:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:f0200000-f023ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 88:9f:fa:4d:4a:9f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-31-generic-pae firmware=N/A ip=192.168.1.244 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:f0100000-f010ffff

```

**if config -a**

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1680 (1.6 KB)  TX bytes:1680 (1.6 KB)

wlan0     Link encap:Ethernet  HWaddr 88:9f:fa:4d:4a:9f  
          inet addr:192.168.1.244  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::8a9f:faff:fe4d:4a9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5852 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5419 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6008211 (6.0 MB)  TX bytes:1193790 (1.1 MB)
```

**dmesg | grep e1000**
```
[ 1177.023738] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
[ 1177.023746] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
```

---

### Post by jchiso on 2012-01-28
No hope at all?

---


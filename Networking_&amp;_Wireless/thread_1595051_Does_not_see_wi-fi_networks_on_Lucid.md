---
title: "Does not see wi-fi networks on Lucid"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by zhaber on 2010-10-12
Hi, i have an acer aspire 7551, and trying to setup wireless. The WI-FI indicator is turned off. Here is the basic output that i get:

```
ubuntu@ubuntu:~/Desktop$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:26:2d:ac:e9:e5
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 memory:d0200000-d020ffff
  *-network DISABLED
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 78:e4:00:fc:7b:c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0300000-d030ffff
[CODE]
```
ubuntu@ubuntu:~/Desktop$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:26:2d:ac:e9:e5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8808 (8.8 KB)  TX bytes:8808 (8.8 KB)[/CODE]

---

### Post by Iowan on 2010-10-12
**ifconfig -a** should show wlan0. 
Dunno if [this]("http://ubuntuforums.org/showthread.php?t=1564615") one might help...

---

### Post by zhaber on 2010-10-12
Thanks for the answer. But checking "Connect to wireless and ethernet networks" did not help.
```

iwconfig -a 

wlan0 Link encap:Ethernet ....
           Broadcast Multicast ...

```
Maybe I need somehow to turn on wi-fi manually to move from disabled state, or it means that drivers are not correct?

---

### Post by dineshs on 2010-10-13
Hope enable wireless is ticked(Rightclick NM icon on top right of the panel)

---


---
title: "Lenovo B470 - wired network not working on Ubuntu 12.04"
date: 2013-05-11
forum: Networking &amp; Wireless
---

### Post by gopaleen on 2013-05-11
Hi, 
I'm trying to connect on a Lenovo B470 running Ubuntu 12.04. The ethernet cable seems to connect fine and there is a green LED with a blinking orange LED. And my network connections recognizes a "wired connection 1" but won't connect. The icon just constantly says it's connecting but nothing happens.


Any help would be greatly appreciated.

ifconfig
> eth0      Link encap:Ethernet  HWaddr f0:de:f1:4b:40:86  
          inet6 addr: fe80::f2de:f1ff:fe4b:4086/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29313 errors:0 dropped:0 overruns:0 frame:0
          TX packets:619 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1866251 (1.8 MB)  TX bytes:143130 (143.1 KB)
          Interrupt:41 Base address:0x4000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9628 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9628 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:765304 (765.3 KB)  TX bytes:765304 (765.3 KB)


wlan0     Link encap:Ethernet  HWaddr 68:a3:c4:40:70:ab  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


sudo lshw -C network
>   *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 68:a3:c4:40:70:ab
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-35-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0500000-d050ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: f0:de:f1:4b:40:86
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:2000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff




Thanks!

---


---
title: "Wired Connection Fails After Crash"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by Yashar.Hez on 2012-01-12
Hi 
 My laptop had a crash a while ago and after restarting it took a while to fix disk errors. Everything runs normally since then but the wired internet connection does not work at all. I can connect through wireless without any difficulty though. Here's the output of a few command (PS. I don't understand anything):


sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:26:82:c4:bd:5b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=10.2.34.118 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:16 memory:d3000000-d3003fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: c8:0a:a9:fa:5d:83
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:45 ioport:2000(size=256) memory:d1004000-d1004fff memory:d1000000-d1003fff memory:d1010000-d101ffff







> ifconfig
eth0      Link encap:Ethernet  HWaddr c8:0a:a9:fa:5d:83  
          inet6 addr: fe80::ca0a:a9ff:fefa:5d83/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2596 errors:0 dropped:454 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:395116 (395.1 KB)  TX bytes:5382 (5.3 KB)
          Interrupt:45 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:26:82:c4:bd:5b  
          inet addr:10.2.34.118  Bcast:10.2.35.255  Mask:255.255.254.0
          inet6 addr: fe80::226:82ff:fec4:bd5b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48578 errors:0 dropped:0 overruns:0 frame:260722
          TX packets:241236 errors:22 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16904366 (16.9 MB)  TX bytes:208183214 (208.1 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:961 errors:0 dropped:0 overruns:0 frame:0
          TX packets:961 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31469 (31.4 KB)  TX bytes:31469 (31.4 KB)

---


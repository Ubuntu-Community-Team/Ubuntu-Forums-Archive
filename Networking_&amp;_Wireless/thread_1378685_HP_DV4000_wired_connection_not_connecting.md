---
title: "HP DV4000 wired connection not connecting"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by iczer2001 on 2010-01-11
I have the latest version of ubuntu on an HP dv4000 laptop fully updated. wireless worked out of the box. but the wired connection wont start. Problem is with the ubuntu install not the network. But i dont know how to configure it to work. please help. below is the output for two commands that I ran, I typed **:**:**  for MAC address. thanks.

command: ifconfig
eth0      Link encap:Ethernet  HWaddr 00:**:**:**:**:**  
          inet6 addr: fe80::***:****:***:****/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1614 (1.6 KB)  TX bytes:7434 (7.4 KB)
          Interrupt:20 Base address:0x3000 

eth1      Link encap:Ethernet  HWaddr 00:**:**:**:**:** 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3534 (3.5 KB)  TX bytes:5071 (5.0 KB)
          Interrupt:20 Memory:b0106000-b0106fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

command: sudo lshw -C network
  *-network:0 DISABLED    
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth1
       version: 05
       serial: 00:**:**:**:**:**
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=128 link=no maxlatency=24 mingnt=3 multicast=yes wireless=radio off
       resources: irq:20 memory:b0106000-b0106fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:**:**:**:**:**
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:20 ioport:3000(size=256) memory:b0109400-b01094ff


anybody see any problem as to why my wired NIC wont work? thanks a lot

---

### Post by iczer2001 on 2010-01-11
is there more info needed for my problem? i really hate to bug you guys but im really in a bind here, cant access my network through wired and I cant find out why. I used to run a ubuntu about 1 year ago and never had a problem, just did a fresh install of the latest version and wireless works but wired doesn't. :( any ideas?

also several other windows computers work fine on the same network and even the same network cable. thanks for your help

---


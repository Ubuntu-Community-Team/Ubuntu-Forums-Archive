---
title: "Problems with dv6000 ethernet!"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by reltx on 2009-04-11
After installing Ubuntu 8.10, ethernet worked and automatically connected each time, although wifi could never connect.  So I fixed the wifi issue but now Ubuntu won't recognize my ethernet and I can't connect to the internet. 

Under connections wired network is grayed out and it says that wired network "device is unmanaged"???  PLEASE HELP!

Specs: HP dv6105ca

---

### Post by reltx on 2009-04-11
m@m-laptop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:14:a5:f6:8f:c7
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 ip=192.168.1.111 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c2:7a:6e:69:56:e3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


m@m-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:22:33:44:55  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:22ff:fe33:4455/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1309 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:925867 (925.8 KB)  TX bytes:307225 (307.2 KB)
          Interrupt:20 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:14:a5:f6:8f:c7  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fef6:8fc7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19940 errors:0 dropped:0 overruns:0 frame:13872
          TX packets:15958 errors:30 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26049848 (26.0 MB)  TX bytes:2152459 (2.1 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16616 (16.6 KB)  TX bytes:16616 (16.6 KB)

m@m-laptop:~$

---


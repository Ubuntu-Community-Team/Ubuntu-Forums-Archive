---
title: "can't detect any wireless after upgrade the core"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by yujiao on 2009-09-14
Hi,

Can anybody help me with the wireless detection? After i made an upgrade to the core, Ubuntu can't detect any wireless.

the output of ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:1a:6b:ce:cb:a6  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:6bff:fece:cba6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21229 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:16018790 (16.0 MB)  TX bytes:4444482 (4.4 MB)
          Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5432 (5.4 KB)  TX bytes:5432 (5.4 KB)


the output of iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

the output of lshw -C network
*-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1a:6b:ce:cb:a6
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=0.3-0 ip=192.168.1.5 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: be:a1:6f:97:da:eb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
long@yujiao-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:6b:ce:cb:a6  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:6bff:fece:cba6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21229 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:16018790 (16.0 MB)  TX bytes:4444482 (4.4 MB)
          Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5432 (5.4 KB)  TX bytes:5432 (5.4 KB)

If you need any more output, please need me know.

Thanks a lot.

---


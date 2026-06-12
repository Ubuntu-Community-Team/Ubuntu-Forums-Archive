---
title: "Problem with network in ubuntu"
date: 2011-03-31
forum: Networking &amp; Wireless
---

### Post by vinte on 2011-03-31
I'm a newbie in ubuntu. 
My pc's IP address: 192.168.8.100
I ping a router' IP address: 192.168.8.202, result:

PING 192.168.8.202 (192.168.8.202) 56(84) bytes of data.
64 bytes from 192.168.8.202: icmp_req=1 ttl=70 time=950 ms
64 bytes from 192.168.8.202: icmp_req=2 ttl=70 time=1008 ms
64 bytes from 192.168.8.202: icmp_req=3 ttl=70 time=943 ms
64 bytes from 192.168.8.202: icmp_req=4 ttl=70 time=1008 ms
64 bytes from 192.168.8.202: icmp_req=5 ttl=70 time=82.1 ms
64 bytes from 192.168.8.202: icmp_req=6 ttl=70 time=1008 ms
64 bytes from 192.168.8.202: icmp_req=7 ttl=70 time=927 ms
64 bytes from 192.168.8.202: icmp_req=8 ttl=70 time=730 ms
64 bytes from 192.168.8.202: icmp_req=9 ttl=70 time=928 ms
64 bytes from 192.168.8.202: icmp_req=10 ttl=70 time=1927 ms

--- 192.168.8.202 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9021ms
rtt min/avg/max/mdev = 82.179/951.523/1927.578/420.503 ms, pipe 2

It's not stable. But when I switch to windows xp and ping router, the delay time is low and stable.
Someboby helps me a solution for my ubuntu 10.10
 
#ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:58:c9:c5:1c  
          inet addr:192.168.8.8  Bcast:192.168.8.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18513 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40121363 (40.1 MB)  TX bytes:1658407 (1.6 MB)
          Interrupt:16 Memory:ee000000-ee020000 

#lshw -C network
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:15:58:c9:c5:1c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=0.5-1 ip=192.168.8.8 latency=0 multicast=yes
       resources: irq:44 memory:ee000000-ee01ffff ioport:2000(size=32)

Thanks a mil.

---


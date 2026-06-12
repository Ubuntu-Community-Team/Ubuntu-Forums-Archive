---
title: "problem with my wireless"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by afroditixen on 2009-05-18
i have a problem with my wireless .my computer cannot find anywireless  network,i suppose that there is a problem with the driver but i don't know which driver is apropriate to my computer!any help?

---

### Post by Peter09 on 2009-05-18
Can you post the output of the terminal commands

```
lshw -C network
```
and
```
ifconfig
```

---

### Post by afroditixen on 2009-05-18
i did it and this is what is written.now what do i have to do??
thank you very much!!! 


root@afroditi-laptop:/home/afroditi# lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:05:07.0
       logical name: eth0
       version: 10
       serial: 00:1d:60:f2:e6:68
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.140 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:44:1a:a0:13
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g
root@afroditi-laptop:/home/afroditi# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:60:f2:e6:68  
          inet addr:192.168.0.140  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fef2:e668/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:778 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:543164 (530.4 KB)  TX bytes:163953 (160.1 KB)
          Interrupt:16 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62700 (61.2 KB)  TX bytes:62700 (61.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:1a:a0:13  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@afroditi-laptop:/home/afroditi#

---


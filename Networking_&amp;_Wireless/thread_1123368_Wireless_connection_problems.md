---
title: "Wireless connection problems"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by dattandai on 2009-04-12
Hey, I'm a new user of these forums and Ubuntu, so be nice. ^_^

Anyway, I'm having a problem connecting to my wireless network through Ubuntu. The laptop I'm trying to install it on is an old Acer Aspire 3690. When clicking on the network connections in the top panel, "Wired Network", "Auto eth0" and "Wireless Networks" are greyed out. I've tried an ethernet cable but Ubuntu just spends forever trying to connect. 

Please help. ><

---

### Post by t0mppa on 2009-04-12
To get an idea of what's the real problem, plug in the ethernet cable, open up a terminal, run these commands and post the results:
```
lspci | grep Ethernet
ifconfig
sudo lshw -C network
```

---

### Post by Kevbert on 2009-04-12
Do you have a front panel wireless switch ? Try switching it once as the wireless light may not be accurate (it may suggest wireless is on when in fact it isn't). It may be the same with bluetooth (if you have it).

---

### Post by dattandai on 2009-04-12
This is what I got. 

hoa@hoa-laptop:~$ lspci | grep Ethernet
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
hoa@hoa-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:60:a6:f3  
          inet6 addr: fe80::216:d4ff:fe60:a6f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8116 (8.1 KB)  TX bytes:2494 (2.4 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

hoa@hoa-laptop:~$ 
hoa@hoa-laptop:~$ lspci | grep Ethernet
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
hoa@hoa-laptop:~$ sudo lshw -C network
[sudo] password for hoa: 
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:60:a6:f3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:cf:b6:c6:8a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ae:11:81:42:ce:8d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
hoa@hoa-laptop:~$

---

### Post by dattandai on 2009-04-12
> **Kevbert said:**
> Do you have a front panel wireless switch ? Try switching it once as the wireless light may not be accurate (it may suggest wireless is on when in fact it isn't). It may be the same with bluetooth (if you have it).

Yeah, I've tried. Nothing happens. ><

---

### Post by t0mppa on 2009-04-12
See this thread: [http://ubuntuforums.org/showthread.php?t=963978]("http://ubuntuforums.org/showthread.php?t=963978") for troubleshooting your wireless issues.

Incase you didn't notice it yourself, your wireless chip is: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller

---


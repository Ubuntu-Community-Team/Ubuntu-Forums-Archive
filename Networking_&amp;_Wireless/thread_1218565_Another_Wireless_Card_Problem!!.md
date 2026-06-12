---
title: "Another Wireless Card Problem!!"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by Ofrepose on 2009-07-20
Hey guys, I am trying to get off of Windows again due to...it being fail. Anyways, having trouble getting my wireless card to work in Ubuntu. Here is the details from Terminal with sudo lshw -c network:

   *-network:0             
   
         description: Network controller
   
         product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
   
         vendor: Broadcom Corporation
   
         physical id: 0
   
         bus info: pci@0000:01:00.0
   
         version: 02
   
         width: 32 bits
   
         clock: 33MHz
   
         capabilities: bus_master
   
         configuration: driver=b43-pci-bridge latency=32 module=ssb
   
    *-network:1
   
         description: Ethernet interface
   
         product: 82562EZ 10/100 Ethernet Controller
   
         vendor: Intel Corporation
   
         physical id: 8
   
         bus info: pci@0000:01:08.0
   
         logical name: eth0
   
         version: 02
   
         serial: 00:13:20:61:f7:fd
   
         size: 10MB/s
   
         capacity: 100MB/s
   
         width: 32 bits
   
         clock: 33MHz
   
         capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
   
         configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
   
    *-network:0 DISABLED
   
         description: Ethernet interface
   
         physical id: 1
   
         logical name: pan0
   
         serial: b2:8c:7e:8a:29:22
   
         capabilities: ethernet physical
   
         configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
   
    *-network:1 DISABLED
   
         description: Wireless interface
   
         physical id: 2
   
         logical name: wlan0
   
         serial: 00:12:17:69:f2:4d
   
         capabilities: ethernet physical wireless
   
         configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
   
  

I have been trying to get this work for literally a day and a half!! Any help would be more than appreciated!

---

### Post by superprash2003 on 2009-07-21
post output of
1)sudo iwlist scanning
2)iwconfig

 is this a laptop or desktop?

---


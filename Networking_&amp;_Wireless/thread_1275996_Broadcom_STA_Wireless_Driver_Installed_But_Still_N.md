---
title: "Broadcom STA Wireless Driver Installed But Still No Detected Wireless Netowrks"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by mfernando on 2009-09-26
I have recently installed Ubuntu 9.04 and loaded the Broadcom STA Wireless Driver when prompted by the system. The system does not detect any wireless connections and only shows the wired connection, and have rebooted a number of times since. I know for certain that are about 20 connections in range, including my own.

When I run the **lspci **command I get:
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)

When I run the **ifconfig** command I get:
eth0      Link encap:Ethernet  HWaddr 00:1b:24:6a:38:d7  
          inet addr:192.168.2.16  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe6a:38d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2524570 (2.5 MB)  TX bytes:618589 (618.5 KB)
          Interrupt:20 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:7e:fa:b5  
          inet6 addr: fe80::21a:73ff:fe7e:fab5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

When I run the **lshw -c network **command I get:
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:1a:73:7e:fa:b5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8e:9f:5b:a0:06:99
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

When I run the **iwconfig** command I get:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.

When I go to **System -> Administration -> Hardware Drivers** shows:
[INDENT] Broadcom STA wireless driver
with a green button for the STA driver which
 "is activated and currently in use"
It says the STA driver is tested by Ubuntu developers and the license is
 proprietary.
[/INDENT]

---

### Post by mfernando on 2009-09-26
Sorry I found what the problem was. The wiki switch was set to OFF.

---

### Post by astembridge on 2009-09-26
> **mfernando said:**
> Sorry I found what the problem was. The wiki switch was set to OFF.

PLEASE explain what you meant by "the wiki switch was set to OFF"

I have been without wireless for two weeks now.  Your post exactly mirrors what I am experiencing now. 

please please reply and let us know what you did to resolve.  thank you.

---

### Post by mfernando on 2009-10-17
Sorry, I meant the wifi switch on my machine.

---


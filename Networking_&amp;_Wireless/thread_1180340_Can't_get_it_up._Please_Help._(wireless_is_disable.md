---
title: "Can't get it up. Please Help. (wireless is disabled)"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by jimmygo on 2009-06-06
I have a fresh install of Ubuntu 9.04 on a Dell Inspiron 630m. In the past (Ubuntu 7.10 or so) wireless worked out of the box on this machine, so suspected to this time. 

In Admin --> Network Tools, Wireless Interface (wlan0) is listed as State: Inactive. I imagine this is no good, but can't see a way to change the state.

Function - F2 doesn't appear to have any effect. Have seen reports that the command doesn't work for this laptop.

I have googled around and have seen people always want the following info (controller, lshw, and ifconfig). Also have included a screenshot of network tools dialog.

Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

lshw -C network
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:89:9d:fb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


jenn@jenn-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:a6:44:16  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fea6:4416/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:115942 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:167392536 (167.3 MB)  TX bytes:6203135 (6.2 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7404 (7.4 KB)  TX bytes:7404 (7.4 KB)

---

### Post by jimmygo on 2009-06-06
Coffeeaddict helped me out over in this thread: [http://ubuntuforums.org/showthread.php?t=1178739](http://ubuntuforums.org/showthread.php?t=1178739)

I simply had to activate the driver in System --> admin --> hardware drivers.

Thanks Ubuntu forums!

---


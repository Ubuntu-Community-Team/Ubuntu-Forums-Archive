---
title: "How do i connect to internet?"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by eleb on 2009-08-05
Typing lspci
 
```
lspci |grep Ethernet
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (CNR) Ethernet Controller (rev 82)
```
 
It's my old desktop, and i did install ubuntu 9.04 today.
 
I couldn't connect to internet!
 
 
Typing lshw
 
```
sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: 82801DB PRO/100 VE (CNR) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 82
       serial: 00:20:ed:58:c0:86
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 76:e7:5b:80:13:d7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```
 
Typing ifconfig
 
```
sudo ifconfig
[sudo] password for linux: 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3424 (3.4 KB)  TX bytes:3424 (3.4 KB)
 

```
 
 
Plz, Somebody help me!

---

### Post by realzippy on 2009-08-05
You use a router or only a modem?

---

### Post by realzippy on 2009-08-05
forget first post.
*-network DISABLED !!!!!!!!

Did you enable auto eth0 in networkmanager?

---

### Post by Bucky Ball on 2009-08-05
Can you plug an ethernet cable in and get your updates? If you just installed today, there is a good chance there are restricted drivers for your wireless hardware, but you need to download them (they don't come with Ubuntu install because they are third-party and you need to personally agree to the conditions when you install them). The best way to do that is to plug in and get your updates.

If there are drivers available, you will be offered them and then invited to choose a network and input the security info etc.

---


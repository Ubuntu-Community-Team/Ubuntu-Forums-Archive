---
title: "BCM4318 | WiFi connection lost after several minutes"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by msm120 on 2010-10-13
I re-imaged my laptop away from 9.10 to 10.10 on Sunday.  For the past year, I've had no problems with WiFi connectivity.  Then, after installation, I find I intermittently lose WiFi connectivity.  

When this happens, I use the NetworkManager Applet 0.8.1 to ensure the wireless session is disconnected, then attempt to re-connect ... nothing happens - the connection icon appears to be re-establishing a connection, only to give up.  Another session is established only after reboot.  (Wait some minutes, then again, it randomly disconnects.)  

I am unable to reliably determine what I'm doing to cause this - i.e., happens during web browsing or podcast downloads via gPodder.  Again, never experienced this issue in 9.10. Here's the info on the card:

lspci
```
Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

Any guidance would be appreciated ... Thank you. // PS - Restricted drivers were installed.

---

### Post by Peter09 on 2010-10-13
can you show the  output of
 
```
lshw -C network
```
 
which should show the driver that you are using. Do this without a wired connection established.
 
also
 
```
ifconfig
```
 
just for completeness.

---

### Post by Peter09 on 2010-10-13
Looks like this is a known problem
 
[http://ubuntuforums.org/showthread.php?t=1390174](http://ubuntuforums.org/showthread.php?t=1390174)

---

### Post by msm120 on 2010-10-13
As requested ... and, thank you for the subsequent reference post ...

**lshw -C network**

  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:10 memory:e0204000-e0205fff
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:6b:42:f1
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:10 memory:e0206000-e0207fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:5b:e7:60
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A ip=0.0.0.0 link=yes multicast=yes wireless=IEEE 802.11bg

**ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:12:3f:6b:42:f1  
          inet6 addr: fe80::212:3fff:fe6b:42f1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14034 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10822 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13110267 (13.1 MB)  TX bytes:2200014 (2.2 MB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:264 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22056 (22.0 KB)  TX bytes:22056 (22.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:5b:e7:60  
          inet addr:0.0.0.0  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fe5b:e760/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1277 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:643927 (643.9 KB)  TX bytes:291815 (291.8 KB)

---


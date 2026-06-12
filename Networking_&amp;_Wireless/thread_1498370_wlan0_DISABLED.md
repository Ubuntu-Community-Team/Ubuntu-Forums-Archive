---
title: "wlan0 DISABLED?"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by jefvel on 2010-05-31
Hello. I've been trying to solve a probably quite common problem for some while now, to connect to the internet with a wireless adapter. Now the thing is, I can't fix it :(

The LEDs on the adapter are all off, and I've tried to use ndiswrapper without no success.

Here's some info:

```

aksel@Burk:~$ sudo lshw -c network
[sudo] password for aksel: 
  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:17 memory:fddfc000-fddfdfff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:30:bd:f5:1e:dc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


aksel@Burk:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:15:58:25:55:f6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:600 errors:0 dropped:0 overruns:0 frame:0
          TX packets:600 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47744 (47.7 KB)  TX bytes:47744 (47.7 KB)



aksel@Burk:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off




```

I have no idea of what to try next.

```
sudo iwconfig wlan0 up
``` doesn't work, it just tells that it can't find that directory or something.

The wireless adapter works just fine in windows, so that it'd be broken is not the case.

I'm very thankful for any help.
Good night.

---


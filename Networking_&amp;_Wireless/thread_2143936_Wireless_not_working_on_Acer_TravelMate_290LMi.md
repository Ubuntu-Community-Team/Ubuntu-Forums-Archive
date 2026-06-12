---
title: "Wireless not working on Acer TravelMate 290LMi"
date: 2013-05-10
forum: Networking &amp; Wireless
---

### Post by Antonio Orvieto on 2013-05-10
I've installed xubuntu 8.04 on an old PC (the kernel was supported)... i simply can't check the "enable wireless" box! The wireless led is also off (on the other hand the wireless switch is on). I tried to use a different os, Linux mint 9.. and the problem is still the same! I tried to use a usb wireless adapter that worked perfectly a Linux Mint 9 PC out of the box....and it did not work.

The following outputs were displayed with the USB wireless adapter not connected

**lshw -C network :**
 ```

 *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:1a:c8:9d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:49:b9:3d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=128 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off

```

**iwconfig**
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by gordintoronto on 2013-05-10
You're playing with really old, not supported versions of Linux. Try Ubuntu 12.04 or Mint 13.

---


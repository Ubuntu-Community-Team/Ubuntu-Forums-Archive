---
title: "My Dell d610 with intel 2200bg can see but not connect to wifi"
date: 2011-11-05
forum: Networking &amp; Wireless
---

### Post by ssout2002 on 2011-11-05
I'm a beginner, I installed 11.10 on this laptop. It was xp and it would connect to my unsecured router, so it seems the hardware is ok.Now it tries to connect, but doesn't. It sees my router along with several neighbors. I tried changing my router to different channels. It must be some setting, but I'm in over my head.
Here is some information that another thread suggested checking.

 ss@ss-Latitude-D610:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:11:43:48:d5:3e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 duplex=full firmware=5751-v3.29a ip=192.168.1.11 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:dfdf0000-dfdfffff
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:eb:1d:d4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:dfcff000-dfcfffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
ss@ss-Latitude-D610:~$ 


What is the next step? thank you in advance

---

### Post by ssout2002 on 2011-11-05
more stuff
this seems to show that the pc can see the access point.
ss@ss-Latitude-D610:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"steve24"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: A0:21:B7:62:BB:B9   
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ss@ss-Latitude-D610:~$ 
ss@ss-Latitude-D610:~$ 
ss@ss-Latitude-D610:~$

---

### Post by ssout2002 on 2011-11-07
im reinstalling xp to confirm the hardware is working

---

### Post by ssout2002 on 2011-11-19
got a diferant wireless router. it works now. i would still like to know why.

---


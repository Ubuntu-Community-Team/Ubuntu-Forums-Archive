---
title: "-NETWORK UNCLAIMED Internet AccessProblem"
date: 2009-07-26
forum: Networking &amp; Wireless
---

### Post by deepakdhar on 2009-07-26
I am new user to Ubuntu 9.04 , Installed it now DUAL boot with WinXP , Not able to connect to internet through Ubuntu
Gone through the Mails and saw some common commands being asked to run :
Here is a op of 2 such commands,

ifconfig :
-------------

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8404 (8.4 KB)  TX bytes:8404 (8.4 KB)

pan0      Link encap:Ethernet  HWaddr d2:7b:67:99:da:37 
          inet6 addr: fe80::d07b:67ff:fe99:da37/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:804 (804.0 B)

lshw -C network

 *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:b2:eb:65
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network UNCLAIMED
       description: Ethernet controller
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=64 maxlatency=56 mingnt=8
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d2:7b:67:99:da:37
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


In WinXP i don't have to enable or give any auth , Internet is directly conected when i switch on my ADSL Modem
Any help would be appreciated

---


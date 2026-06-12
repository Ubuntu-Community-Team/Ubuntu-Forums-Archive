---
title: "Belkin wireless adapter seen but not working"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by brightbird on 2013-01-07
Hi,

I'm not all that linux- or tech-savvy so please be patient!

My netgear adapter broke so I'm trying to get an old Belkin F5D7051  I had working.

I'm running ubuntu 12.04.1 LTS. Adapter and driver seem to be seen in lshw etc (see below) but its not seeing any networks. Also seems to be disabled when I start up (I got it up using sudo ifconfig wlan0 up).

I use wicd and had uninstalled networkmanager because my netgear adapter didn't like it.


camilla@nabatanzi:~$ sudo lshw -C network 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 10
       serial: 00:90:f5:33:2d:e5
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:11 ioport:2000(size=256) memory:ec005000-ec0050ff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:c6:7e:36
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rndis_wlan driverversion=22-Aug-2005 firmware=Wireless RNDIS device link=no multicast=yes wireless=IEEE 802.11bg

camilla@nabatanzi:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 050d:7051 Belkin Components F5D7051 802.11g Adapter v1000 [Broadcom 4320 USB]
Bus 002 Device 002: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 Webcam
Bus 001 Device 004: ID 0781:556b SanDisk Corp. 

camilla@nabatanzi:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.



Do I need to install a different driver or something?
Ubuntu + wireless drives me nuts, I usually end up spending hours searching for solutions - thought this time I'd try asking people who know more than me! 

thanks

---


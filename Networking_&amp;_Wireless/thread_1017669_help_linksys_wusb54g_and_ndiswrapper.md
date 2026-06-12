---
title: "help linksys wusb54g and ndiswrapper"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by ektorf on 2008-12-21
Help, can not connect using dhclient in terminal
Using ubuntu 8.10 and a linksys wusb54g version 4
I have the following displayed after using different commands in terminal...
 
hector@hector-desktop:~$ ndiswrapper -l 
rt2500usb : driver installed 
device (13B1:000D) present (alternate driver: rt2500usb) 

**********

hector@hector-desktop:~$ lsusb 
Bus 002 Device 005: ID 06e6:c31c Tiger Jet Network, Inc. Composite Device 
Bus 002 Device 004: ID 1307:1169 Transcend Information, Inc. TS2GJF210 JetFlash 210 2GB 
Bus 002 Device 003: ID 1307:0169 Transcend Information, Inc. 
Bus 002 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 005: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader 
Bus 001 Device 003: ID 13b1:000d Linksys WUSB54G Wireless Adapter 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

**********

hector@hector-desktop:~$ sudo dhclient wlan0 
There is already a pid file /var/run/dhclient.pid with pid 7067 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.1.1 
Copyright 2004-2008 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
Listening on LPF/wlan0/00:12:17:84:20:d3 
Sending on LPF/wlan0/00:12:17:84:20:d3 
Sending on Socket/fallback 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5 
No DHCPOFFERS received. 
No working leases in persistent database – sleeping. 

************

hector@hector-desktop:~$ sudo iwconfig 
lo no wireless extensions. 

eth0 no wireless extensions. 

wmaster0 no wireless extensions. 

wlan0 IEEE 802.11bg ESSID:"magiko" 
Mode:Managed Frequency:2.437 GHz Access Point: 00:11:50:5B:29:51 
Bit Rate=2 Mb/s Tx-Power=17 dBm 
Retry min limit:7 RTS thr:off Fragment thr=2352 B 
Encryption key:off 
Power Management:off 
Link Quality=70/100 Signal level:-58 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0 
Tx excessive retries:0 Invalid misc:0 Missed beacon:0 

pan0 no wireless extensions. 

****************

hector@hector-desktop:~$ lshw -c network 
WARNING: you should run this program as super-user. 
*-network:0 
description: Wireless interface 
physical id: 3 
logical name: wlan0 
serial: 00:12:17:84:20:d3 
capabilities: ethernet physical wireless 
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
*-network:1 DISABLED 
description: Ethernet interface 
physical id: 4 
logical name: pan0 
serial: 1a:14:07:58:f9:17 
capabilities: ethernet physical 
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 

What's wrong? I'm new to ubuntu  so I tried to follow the ndiswrapper install step by step

---

### Post by blothian on 2009-01-18
What Version of Ubuntu are you using?

---

### Post by blothian on 2009-01-18
Im using the newest to date i just plugged my Linksys WUSB54G worked perfectly no hesatation i could connect to my network with none of the stupid ndiswrapper or anything!

Thanks Ben

---


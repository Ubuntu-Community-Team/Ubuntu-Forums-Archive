---
title: "No DHCPOFFERS received ENUWI-G2 Encore USB Wireless"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by Kawa800 on 2009-04-03
I have Ubuntu 8.10.  I have used the following technique to connect to my wireless network in the past.  My Linksys USB adapter died so I replaced with Encore ENUWI-G2 USB adapter.  It was a good deal on NewEgg and a few of the reviews said they got it to work in Ubuntu so I figured I would give it a shot.  I removed the Linksys driver from Ndiswrapper and installed Encore driver from cd.  When I say install, I mean i browsed to the .inf file to add driver using ndiswrapper.  I tried the XP and the Windows 2000.  Both gave same results.  I thought I should use the key open command, but it didn't seem to like it so I tried restricted with same results.  I know the hardware is working because I installed it on my XP machine and it worked fine.  I know the router is fine because there is currently an XP PC, Ubuntu Laptop and Wii connected to it via wireless.  Here is what I typed in terminal:


david@KidsPC:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 3c900B-TPO Etherlink XL [Cyclone]
       vendor: 3Com Corporation
       physical id: b
       bus info: pci@0000:02:0b.0
       logical name: eth0
       version: 04
       serial: 00:01:02:82:af:96
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x latency=64 maxlatency=48 mingnt=10 module=3c59x multicast=yes
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 22:05:c7:fb:51:5e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 3
       logical name: wlan1
       serial: 00:08:54:92:a0:35
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8187b driverversion=1.53+Realtek Semiconductor Corp. multicast=yes wireless=IEEE 802.11g
david@KidsPC:~$ sudo ifconfig wlan1 down
david@KidsPC:~$ sudo dhclient -r wlan1
There is already a pid file /var/run/dhclient.pid with pid 6244
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan1/00:08:54:92:a0:35
Sending on   LPF/wlan1/00:08:54:92:a0:35
Sending on   Socket/fallback
david@KidsPC:~$ sudo ifconfig wlan1 up
david@KidsPC:~$ sudo iwconfig wlan1 essid "Narnia"
david@KidsPC:~$ sudo iwconfig wlan1 key xxxxxxxxxxxxxxxxxxxxxxxxxx
david@KidsPC:~$ sudo iwconfig wlan1 key open
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan1 ; Invalid argument.
david@KidsPC:~$ sudo iwconfig wlan1 key restricted
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan1 ; Invalid argument.
david@KidsPC:~$ sudo iwconfig wlan1 mode Managed
david@KidsPC:~$ sudo dhclient wlan1
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan1/00:08:54:92:a0:35
Sending on   LPF/wlan1/00:08:54:92:a0:35
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
david@KidsPC:~$ 

Anyone have any suggestions?

---


---
title: "Can't get TEW-424UB Wireless Adapter to Work in Hardy"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by ahorne12 on 2009-08-20
Hi All,

   I just got internet set up at my new place, and can't go wired.  I have an old USB wireless adapter that I'm having trouble getting to work.  It's the TEW-424UB Adapter from Trendnet.  My apologies if this has been solved elsewhere; if so, maybe someone could point me in that direction?  I've tried searching the forums, and came across this one:

[http://ubuntuforums.org/showthread.php?t=1187250&highlight=tew-424ub](http://ubuntuforums.org/showthread.php?t=1187250&highlight=tew-424ub)

   I followed the guy's suggestions, but still can't get it to work.  I've managed to get ndiswrapper and the driver installed based on the following out of terminal:

andrew@Rob:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: c
       bus info: pci@0000:05:0c.0
       logical name: eth1
       version: 13
       serial: 00:11:d8:9c:8a:a3
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=32 maxlatency=31 mingnt=23 module=skge multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:40:f4:e4:f2:f0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+sis163u driverversion=1.52+TRENDnet,11/02/2005,5.1.103 multicast=yes wireless=IEEE 802.11g

Then I went ahead and set up the DDIS, key, etc...but when I did the last command (sudo dhclient wlan0), even when I tried resetting (unplugging) the modem as suggested in the thread, I get the following message about the connection "sleeping":

There is already a pid file /var/run/dhclient.pid with pid 6641
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:40:f4:e4:f2:f0
Sending on   LPF/wlan0/00:40:f4:e4:f2:f0
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

The last thing I tried was looking at the sticky in the networking forum about ndiswrapper troubleshooting (not sure if it applies to wireless adapters as well as cards though), and when I check the dmesg output, I get a flurry of messages telling me the link is not ready:

andrew@Rob:~$ dmesg | grep -e ndis -e wlan
[   51.890881] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   52.267162] ndiswrapper: driver sis163u (TRENDnet,11/02/2005,5.1.1039.1050) loaded
[   52.692315] wlan0: ethernet device 00:40:f4:e4:f2:f0 using NDIS driver: sis163u, version: 0x1000000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0457:0163.F.conf
[   52.693454] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   52.698855] usbcore: registered new interface driver ndiswrapper
[   76.352301] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  358.153260] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  371.986230] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  382.187833] wlan0: no IPv6 routers present
[  885.296289] ndiswrapper: device wlan0 removed
[  890.763136] ndiswrapper: driver sis163u (TRENDnet,11/02/2005,5.1.1039.1050) loaded
[  891.193121] wlan0: ethernet device 00:40:f4:e4:f2:f0 using NDIS driver: sis163u, version: 0x1000000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0457:0163.F.conf
[  891.195241] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  891.210218] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Does anyone know how to solve this, from experience with the same problem or just being better at Linux than me.  Perhaps there's something I'm overlooking in the process, or a clue I'm missing in the details.  I'll take either at this point.  Thanks in advance for your help.

Andrew

---


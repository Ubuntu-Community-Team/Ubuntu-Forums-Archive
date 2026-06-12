---
title: "RT61 Drivers with Ubuntu 10.10 (Maverick) 64bit"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by extendon on 2010-12-04
I am trying to get rt61 drivers working for my 64bit installation. (uname -r .6.35-22-generic)
 the card is RaLink RT2561/RT61 802.11g PCI
 I have removed the legacy rt61pci and replaced with the Ralink 1.1.2.6 drivers from the website
 compilation and loading the driver worked.  updated the rt61sta.dat
 however when i try to scan the network i get

 # iwlist ra0 scan
ra0       Failed to read scan data : Argument list too long
the other strange thing is that sometime iwlist works and shows me an available network.
 and

# dhclient ra0 
There is already a pid file /var/run/dhclient.pid with pid 2486
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/ra0/00:a1:b0:30:0d:4d
Sending on   LPF/ra0/00:a1:b0:30:0d:4d
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


 # iwconfig
lo        no wireless extensions.
 eth0      no wireless extensions.
 ra0       RT61 Wireless  ESSID:""
          Mode:Auto  Frequency:2.412 GHz  Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

 Have read through the forums and found nothing relevant to  this situation.
 Can anyone advise on best option for this card and distro?

---


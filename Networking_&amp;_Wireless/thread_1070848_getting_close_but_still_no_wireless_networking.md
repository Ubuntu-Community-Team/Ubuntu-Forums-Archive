---
title: "getting close but still no wireless networking"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by bigbandwith on 2009-02-15
I can connect via  ethernet on kubuntu 8.10 but no wireless still. I successfully downloaded and installed ndiswrapper and my corresponding drivers.  I can see my ESSID and my network strength, but it still says deactivated.  After following several other posts, here are some of my terminal results:

space@space-desktop:~$ sudo lshw -C network
[sudo] password for space:                 
  *-network:0                              
       description: Ethernet interface     
       product: SiS900 PCI Fast Ethernet   
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4                          
       bus info: pci@0000:00:04.0              
       logical name: eth0
       version: 91
       serial: 00:17:31:75:c6:bf
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.1.8 latency=64 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: wmaster0
       version: 01
       serial: 00:12:17:7e:59:ff
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: de:67:38:cc:31:12
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
space@space-desktop:~$

Then I get this trying to get an IP

space@space-desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 5486
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:12:17:7e:59:ff
Sending on   LPF/wlan0/00:12:17:7e:59:ff
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
space@space-desktop

I don't want to give up ...yet.

---

### Post by bigbandwith on 2009-02-15
bump, don't want this thread to get buried.
Thanks!!

---


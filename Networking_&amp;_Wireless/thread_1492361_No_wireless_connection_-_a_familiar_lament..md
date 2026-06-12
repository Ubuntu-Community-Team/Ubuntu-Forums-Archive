---
title: "No wireless connection - a familiar lament."
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by Kalisthen on 2010-05-24
Backstory:

Earlier today my computers XP installation went **** up, and when I reached for the install disc to run chkdsk to fix the errors, I couldnt use that because a file was missing. I remembered I had an old Hardy Heron livecd lying around, and I could use that as a temporary solution. I got curious about the new release, and installed and upgraded from virgin 8.04 to virgin 10.04, and thats where my problems started.

As with a lot of other people, I connect through a router to the internet with a wireless card. After entering the key numerous times, no internet connection.

I have already tried the fix of:

>gksudo gedit /etc/modprobe.d/blacklist.conf

 and blacklisting rt2x00usb, rtsx00lib and rt2800usb, with no effect.

I also tried the following:

chris@chris-desktop:~$ sudo lshw -c network
[sudo] password for chris: 
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:0a:13:cc:b9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


chris@chris-desktop:~$ sudo mii-tool
SIOCGMIIPHY on 'eth0' failed: Operation not supported
no MII interfaces found


chris@chris-desktop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:1b:b9:ef:04:59
Sending on   LPF/eth0/00:1b:b9:ef:04:59
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
chris@chris-desktop:~$ 


I would appreciate any and all help anyone could give me, otherwise I have to reinstall XP and I dont really want to be using an OS thats four or five years out of date. :(

---


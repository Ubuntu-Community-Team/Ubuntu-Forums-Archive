---
title: "Almost there- Wireless problem broadcom 4318 AMD64 alt install"
date: 2006-07-05
forum: Networking &amp; Wireless
---

### Post by abstract51 on 2006-07-05
Hello:

I could use some help to get me over the goal line on connecting with my wireless connection.   I installed the 64bit drivers for the 4318 (bcmwl5).
I have an AMD 64 Athlon Gateway 7510GX and I installed Ubuntu with the amd64 alternate install cd.

ndiswrapper -l says my driver is installed and working

```
sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
```

My wireless light is on.  I can toggle it on and off as well.  Couldn't do this previously until I installed the amd 64 bit drivers for broadcom 4318.

The network manager gui says that both my network settings are active.  Wired is eth0 and Wireless is eth1.  I only have a hard wired router.  However, by clicking on my network settings icon on the top right bar, I can see both unsecured and secured wireless networks in my neighborhood.  With XP, I can easily connect to a neighbor's unsecured wireless network but with Ubuntu I can't.  BTW, I don't poach my neighbor's wireless connection since I have my own wired broadband.  I just leverage this opportunity to test my ability to connect to an unsecured wireless network.  Like I wrote earlier, I can connect easily to this network with XP but not with Ubuntu.

Here is my iwconfig output...

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate=11 Mb/s   Tx-Power:25 dBm
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

Output from running lspci | grep Broadcom

```
0000:03:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

Output from /etc/network/interfaces

```
# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp



iface eth1 inet dhcp

auto eth1



auto eth0
```

Output from /etc/init.d/networking restart says I have a problem with eth1 (wireless) DHCP


```
* Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:03:25:35:4c:3b
Sending on   LPF/eth0/00:03:25:35:4c:3b
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:14:a5:07:12:c4
Sending on   LPF/eth1/00:14:a5:07:12:c4
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.203 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:14:a5:07:12:c4
Sending on   LPF/eth1/00:14:a5:07:12:c4
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:03:25:35:4c:3b
Sending on   LPF/eth0/00:03:25:35:4c:3b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.102 -- renewal in 72553 seconds.
```

I also have wifi-radar installed.  When I run that app and try to connect to an unsecured wireless network it seeks for an IP address and says it has secured one but I can't connect to the network. I notice in my terminal window, i constantly get the following error messages when I run sudo wifi-radar...

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

I can't figure out what's wrong and why I can't connect.  Would appreciate recommendations to get this working.  I'd like to be able to use the wireless feature when I travel.  

Thank you.

---

### Post by gotfoo on 2006-07-06
Start over and use this [howto]("http://www.ubuntuforums.org/showthread.php?t=190177").

---


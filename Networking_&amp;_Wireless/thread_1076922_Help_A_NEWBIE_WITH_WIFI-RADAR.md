---
title: "Help A NEWBIE WITH WIFI-RADAR"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by Pater Puff on 2009-02-21
hey guys

i have a problem with wifi-radar when i try to connect it writes "could not get IP address" what do i do then?

i try'ed this:

```
(user)$ sudo dhclient wlan0
[sudo] password for (user): 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:15:af:9e:98:b9
Sending on   LPF/wlan0/00:15:af:9e:98:b9
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```


and this:

```
(user)~$ ndiswrapper -l
netwg111 : driver installed
rt2860 : driver installed
	device (1814:0781) present (alternate driver: rt2860sta)
```









i use a Zepto Zpro2 wireless card (chipset should be rt2860)

---


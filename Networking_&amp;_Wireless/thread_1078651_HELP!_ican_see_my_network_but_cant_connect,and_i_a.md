---
title: "HELP! ican see my network but cant connect,and i am in the middle of computer projekt"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by Pater Puff on 2009-02-23
hi everybody

i have a BIG problem! i cant get network connection!

i am using Wifi-radar and wenn i try to connect it says that: ```
could not get IP address
```


my questions:

1) what do i write in the WPA "driver" sektion (I am not the admin over the networks i use (my university and my parrents home) it is WPA which is using both places)

2) when I write ndiswrapper - l it says: ```
rt2860 : driver installed
	device (1814:0781) present (alternate driver: rt2860sta)
```
is this correct?

3)what does this mean: ```
t:~$ sudo wifi-radar -d
[sudo] password for peter: 
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
Unsupported driver 'ipw'.

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:15:af:9e:98:b9
Sending on   LPF/wlan0/00:15:af:9e:98:b9
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Could not get IP address!
peter@pedens-put:~$ sudo wifi-radar
peter@pedens-put:~$ sudo wifi-radar -d
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
Unsupported driver '-P'.

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:15:af:9e:98:b9
Sending on   LPF/wlan0/00:15:af:9e:98:b9
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Could not get IP address!

```


4)what can i do to get internet???

---


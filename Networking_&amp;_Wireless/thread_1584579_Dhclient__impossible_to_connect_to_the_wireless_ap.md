---
title: "Dhclient : impossible to connect to the wireless ap"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by FluidBlow on 2010-09-29
Hello everybody.

First of all, i'm using the Hercules HWNUM-300 (usb wifi dongle) on ubuntu 64 bits. I use the RTL8192SU drivers from Realtek.

My problem is: the network manager see the ap's and recognize my usb dongle, but when I try connecting, it seems that it can't connect.

When I do a "sudo dhclient wlan0", i get these messages :
```
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:08:d3:82:25:fd
Sending on   LPF/wlan0/00:08:d3:82:25:fd
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```And it stops.

What's wrong ?

Thank you for any help.

---


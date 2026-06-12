---
title: "Problems with dhcp on Acer Aspire"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by Prof_Albert on 2006-06-30
Since I updated from breezy to dapper, my WLAN doesn't work properly anymore.
at home everything is OK. I can surf for hours with my WLAN at home.
The problem only occures in the WLAN of the University.
Every ~10 minutes I loose my connection and must re-authenticate.
I think it has something to do with my DHCP-client

```
profalbert@profalbert-laptop:~$ sudo dhclient eth1 -d
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/me:in:em:ac:ad:dr
Sending on   LPF/eth1/me:in:em:ac:ad:dr
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 128.131.200.1
bound to 128.131.200.94 -- renewal in 695 seconds.
DHCPREQUEST on eth1 to 128.131.200.1 port 67
DHCPREQUEST on eth1 to 128.131.200.1 port 67
DHCPREQUEST on eth1 to 128.131.200.1 port 67
DHCPREQUEST on eth1 to 128.131.200.1 port 67
DHCPREQUEST on eth1 to 128.131.200.1 port 67
DHCPREQUEST on eth1 to 128.131.200.1 port 67
DHCPREQUEST on eth1 to 128.131.200.1 port 67
DHCPREQUEST on eth1 to 128.131.200.1 port 67
DHCPREQUEST on eth1 to 128.131.200.1 port 67
DHCPREQUEST on eth1 to 128.131.200.1 port 67
DHCPREQUEST on eth1 to 128.131.200.1 port 67
DHCPREQUEST on eth1 to 128.131.200.1 port 67

```
after 10 minutes there come these DHCPREQUESTs every few seconds.
if I kill the dhclient (Ctrl+C) and restart it I have this output.
```
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

**Corrupt lease file - possible data loss!**
Listening on LPF/eth1/me:in:em:ac:ad:dr
Sending on   LPF/eth1/me:in:em:ac:ad:dr
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 128.131.200.1
bound to 128.131.200.218 -- renewal in 745 seconds.

``` 
and after 10 minutes I'm out again...I have an Acer Aspire 1695 with an Intel 2200bg Wireless.
I also tried reinstalling everything, but didn't work...

tia

---

### Post by dare2dreamer on 2006-09-12
I'm having the same issue on a wired lan coming off a router/cable modem.

Anyone have any thoughts on this?

---

### Post by Prof_Albert on 2006-10-11
I just solved the problem! :-D 
I installed DHCPCD
```
apt-get install dhcpcd
```
and uninstalled dhcp3-client
```
apt-get remove dhcp3-client
```

then I got my IP with
```
dhcpcd eth1
```
and I have it for over an hour now...

---


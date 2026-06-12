---
title: "network won't auto start"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by Piddell on 2009-09-29
Hi there,
I have just upgraded my old IBM P4 to 9.04 (which was very slick).

When I boot up the network sometimes fails to start, and needs a little help:

CODE:
voodooalpaca@voodooalpaca-desktop:~$ sudo dhclient
[sudo] password for voodooalpaca: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/pan0/76:c9:94:f2:f1:f0
Sending on   LPF/pan0/76:c9:94:f2:f1:f0
Listening on LPF/eth0/00:02:55:3b:83:27
Sending on   LPF/eth0/00:02:55:3b:83:27
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.3 from 192.168.1.1
DHCPREQUEST of 192.168.1.3 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.3 from 192.168.1.1
bound to 192.168.1.3 -- renewal in 40404 seconds.
voodooalpaca@voodooalpaca-desktop:~$ 

Now when I was on 6.06LTS all was well, so I know it's not a hardware issue.

Its a standard ethernet connected to a router, which has other machines working at the same time.

Any thoughts?

---

### Post by Iowan on 2009-09-29
Are you using Network Manager for DHCP, or do you have settings in */etc/network/interfaces*? (besides "lo")

---

### Post by Piddell on 2009-10-01
> **Iowan said:**
> Are you using Network Manager for DHCP, or do you have settings in */etc/network/interfaces*? (besides "lo")

its right out of the box!

auto lo
iface lo inet loopback

Phill

---

### Post by Iowan on 2009-10-01
Check [this]("http://ubuntuforums.org/showthread.php?t=1156441") one - *sometimes* it helps...

---


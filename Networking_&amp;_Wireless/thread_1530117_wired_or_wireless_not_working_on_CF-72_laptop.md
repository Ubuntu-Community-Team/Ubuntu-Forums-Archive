---
title: "wired or wireless not working on CF-72 laptop"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by Cyborgoat on 2010-07-13
I have an old CF-72 Panasonic laptop I installed 9.10 and now I'm trying to get it hooked up the the internet.  The connection to my router is fine, I can see and open up  the other computers on my LAN.  The eth0 says it is connected to wired network.  it has a 3com wireless card that shows no light nor does it seem to see it.  Where do I start with this one?
I have looked at several postings didnt see one with both my problems.

Thanks ahead of time..

---

### Post by sheffrem on 2010-07-13
Open the terminal and do sudo su . after you give your password type ifup eth0.
If it give any error try dhclient eth0

---

### Post by Cyborgoat on 2010-07-13
here is what I Get.






root@baxter:/home/billy# dhclient eth0
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:80:45:21:97:f7
Sending on   LPF/eth0/00:80:45:21:97:f7
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---


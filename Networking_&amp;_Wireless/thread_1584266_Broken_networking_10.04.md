---
title: "Broken networking 10.04"
date: 2010-09-28
forum: Networking &amp; Wireless
---

### Post by Jerk1 on 2010-09-28
I'm experiencing the [same problem]("http://ubuntuforums.org/showthread.php?t=1488816") now. Upgraded recently (week and a half) from 9.1 to 10.04 and started finding the network broken, only thing I have found that resets the connection is sudo dhclient, which returns:
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/vboxnet0/0a:00:27:00:00:00
Sending on   LPF/vboxnet0/0a:00:27:00:00:00
Listening on LPF/eth1/00:e0:81:b5:0e:b2
Sending on   LPF/eth1/00:e0:81:b5:0e:b2
Listening on LPF/eth0/00:e0:81:b5:0e:b3
Sending on   LPF/eth0/00:e0:81:b5:0e:b3
Sending on   Socket/fallback
DHCPDISCOVER on vboxnet0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPREQUEST of 192.168.1.4 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.4 from 192.168.1.1
bound to 192.168.1.4 -- renewal in 36885 seconds.


I then have normal internet connection, but other computers on the network are unable to see my shared folders

---

### Post by Iowan on 2010-09-28
Moved to new thread.
Appending to end of [SOLVED] thread may not yield much attention.

---


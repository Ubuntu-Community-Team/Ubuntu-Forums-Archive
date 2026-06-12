---
title: "ubuntu 9.04 starts DHCP server before NETWORK ??? Where SERVICES order ???"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by santos_ramirez on 2009-06-18
I have configured dhcp server and I only can start service manually :

:KS /etc/init.d/dhcp3-server start

--> This start server OK...

But when machine reboots, service starts without eth1 up, so it cannot be started ?

Where can I modify "service" order ? 

Jun 18 15:29:57 pepe-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.1
Jun 18 15:29:57 pepe-desktop dhcpd: Copyright 2004-2008 Internet Systems Consortium.
Jun 18 15:29:57 pepe-desktop dhcpd: All rights reserved.
Jun 18 15:29:57 pepe-desktop dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 18 15:29:57 pepe-desktop kernel: [   28.221460] warning: `dhcpd3' uses 32-bit capabilities (legacy support in use)
Jun 18 15:29:57 pepe-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.1
Jun 18 15:29:57 pepe-desktop dhcpd: Copyright 2004-2008 Internet Systems Consortium.
Jun 18 15:29:57 pepe-desktop dhcpd: All rights reserved.
Jun 18 15:29:57 pepe-desktop dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 18 15:29:57 pepe-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.1
Jun 18 15:29:57 pepe-desktop dhcpd: Copyright 2004-2008 Internet Systems Consortium.
Jun 18 15:29:57 pepe-desktop dhcpd: All rights reserved.
Jun 18 15:29:57 pepe-desktop dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 18 15:29:57 pepe-desktop dhcpd: Wrote 1 leases to leases file.
Jun 18 15:29:57 pepe-desktop dhcpd:
**Jun 18 15:29:57 pepe-desktop dhcpd: Not configured to listen on any interfaces!**

:(---> DHCP Server cannot starts because eth1 is not UP !!!

Jun 18 15:30:00 pepe-desktop NetworkManager: <info>  starting...
**Jun 18 15:30:00 pepe-desktop NetworkManager: <info>  (eth1): new Ethernet device (driver: 'e1000')**
Jun 18 15:30:00 pepe-desktop NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_00_0c_29_65_59_33

---

### Post by Iowan on 2009-06-18
Look in /etc/rc*.d directories.  My server runs at runlevel 2, so it's startup (and shutdown) sequence is in */etc/rc2.d*.  I'm not near my Linux box, so my memory may have the wrong directory - hopefully I'm close.

---

### Post by santos_ramirez on 2009-06-19
:KS Thanks Iowan!
 
I have solved with your help.
 
The problem was that starting links for Network was S50 and for dhcp server S40, so dhcp server started before network, so dhcp server exit inmediatelly.
 
I have changed S40 from dhcp server to S99, but not only in level 3 and level 5. I have changed in all levels, including level 2 as you suggested me.
 
Thank a lot for yor help
 
:popcorn: Ubuntu 9.0.4 is running fine the DHCP server.

---


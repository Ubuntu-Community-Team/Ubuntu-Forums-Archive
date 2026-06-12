---
title: "can't start dhcp3 server"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by Adina on 2009-02-24
When I try to start dhcp server on hardy I get this message: "dhcpd self-test failed. Please fix the config file.
The error was"

But it doesn't say what the error is.. I have tried to search for a solution and it seems like a lot of people have had this problem. I have tried to edit the config file /etc/dhcp3/dhcpd.conf and /etc/init.d/dhcp3-server without any luck. If anyone could explain why dhcp3 server won't start I'll really appreciate it.

---

### Post by kidders on 2009-02-25
Hi there,

> **Adina said:**
> dhcpd self-test failed. Please fix the config file.You'll need to post your config file(s) before we can help you! Your system logs may contain more specific information about what's wrong. You should post anything interesting from there as well.

Incidentally, don't edit /etc/init.d/dhcp3-server. Imo, you should revert any changes you've made.

---

### Post by Iowan on 2009-02-25
I usually make a backup of original config files before editing.  First, it lets me get back to square one; second, it lets me delete comments and unused setup options from the "working" copy. If necessary, I can post a copy of originals for you.

---

### Post by sanemanmad on 2009-02-25
Hi. Please past the contents of these two commands after restarting the dhcp3-server. (sudo /etc/init.d/dhcp3-server restart)

 sudo tail -20 /var/log/daemon.log|grep "dhcpd"
 sudo tail -20 /var/log/syslog|grep "dhcpd"

and also let's the /etc/dhcp3/dhcpd.conf file also

---

### Post by Adina on 2009-02-27
Feb 27 20:03:18 FreeServer dhcpd: All rights reserved.
Feb 27 20:03:18 FreeServer dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Feb 27 20:03:18 FreeServer dhcpd: Internet Systems Consortium DHCP Server V3.0.6
Feb 27 20:03:18 FreeServer dhcpd: Copyright 2004-2007 Internet Systems Consortium.
Feb 27 20:03:18 FreeServer dhcpd: All rights reserved.
Feb 27 20:03:18 FreeServer dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Feb 27 20:03:18 FreeServer dhcpd: Internet Systems Consortium DHCP Server V3.0.6
Feb 27 20:03:18 FreeServer dhcpd: Copyright 2004-2007 Internet Systems Consortium.
Feb 27 20:03:18 FreeServer dhcpd: All rights reserved.
Feb 27 20:03:18 FreeServer dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Feb 27 20:03:18 FreeServer dhcpd: Wrote 0 leases to leases file.
Feb 27 20:03:18 FreeServer dhcpd: 
Feb 27 20:03:18 FreeServer dhcpd: No subnet declaration for eth1 (10.0.0.1).
Feb 27 20:03:18 FreeServer dhcpd: ** Ignoring requests on eth1.  If this is not what
Feb 27 20:03:18 FreeServer dhcpd:    you want, please write a subnet declaration
Feb 27 20:03:18 FreeServer dhcpd:    in your dhcpd.conf file for the network segment
Feb 27 20:03:18 FreeServer dhcpd:    to which interface eth1 is attached. **
Feb 27 20:03:18 FreeServer dhcpd: 
Feb 27 20:03:18 FreeServer dhcpd: 
Feb 27 20:03:18 FreeServer dhcpd: Not configured to listen on any interfaces!


Thank you very much for your replies. I found out I had the same subnet declaration on eth0 and eth1. I changed the subnet for eth1 and dhcp3-server restart went ok.

Thanks again, I really appreciate it!

---

### Post by Iowan on 2009-02-27
Congrats! Come back often - either with problems... or solutions.

---


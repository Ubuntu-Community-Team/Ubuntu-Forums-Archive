---
title: "Family-friendly internet connection"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by ganewbie on 2010-08-24
@ [Detonate]("http://ubuntuforums.org/member.php?u=235933") or anybody who has the knowledge:
I am doing [what you suggested]("http://ubuntuforums.org/showthread.php?t=1494628"), which always work but I have no clue what it means.
1- sudo ifdown eth0
2- sudo ifup --force eth0
The outcome of 1 is:
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...fail!
run-parts: /etc/network/if-down.d/50firestarter exited with return code 2
There is already a pid file /var/run/dhclient.eth0.pid with pid 1523
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/6c:f0:49:b1:7b:85
Sending on   LPF/eth0/6c:f0:49:b1:7b:85
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.15.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

What can I do to fix this issue for good as if I am not home, my family canot do much and stays with no internet.
Helpplease !!!

---

### Post by Detonate on 2010-08-24
I have seen a thread somewhere which officered a permanent fix.  I can't remember if it is on this forum or the Ubuntu forum.  I'll try and see if I can find it.  One quick fix to get rid of the problem is to either disable hibernation, or remove network manage following my instructions here.  Either one would work.

[http://kubuntuforums.net/forums/index.php?topic=3100052.0](http://kubuntuforums.net/forums/index.php?topic=3100052.0)

---

### Post by Iowan on 2010-08-24
Moved to separate thread - linked to [old one]("http://ubuntuforums.org/showthread.php?t=1494628").

---


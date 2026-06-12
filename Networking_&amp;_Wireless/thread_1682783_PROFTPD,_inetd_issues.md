---
title: "PROFTPD, inetd issues"
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by GenericUser on 2011-02-06
I am trying set up an ftp server on Ubuntu 10.10(not the server edition)
I have openbsd-inetd installed
I also have proftpd-basic installed

from an external port scanner i get 
Port 21: File Transfer [Control]

Command$ nmap localhost

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2011-02-06 12:46 EST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00042s latency).
Hostname localhost resolves to 2 IPs. Only scanned 127.0.0.1
rDNS record for 127.0.0.1: localhost.localdomain
Not shown: 997 closed ports
PORT    STATE SERVICE
21/tcp  open  ftp

when I use filezilla to try to access the ftp
i get

Status:	Connecting to 0.0.0.0:21...
Status:	Connection established, waiting for welcome message...
Error:	Connection closed by server
Error:	Could not connect to server
 where I have replaced my ip address on this forum with 0s for security reasons

command$ ps aux
lots of other services....
root      6460  0.0  0.0  10420   800 ?        Ss   10:45   0:00 /usr/sbin/inetd
lots of other services....

---

### Post by GenericUser on 2011-02-18
After a Fresh Install of Ubuntu, inetd, and proftpd, its working well

---


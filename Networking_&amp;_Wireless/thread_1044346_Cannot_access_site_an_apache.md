---
title: "Cannot access site an apache"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by sveri on 2009-01-19
Hi all,

i have Ubuntu 8.10 and apache2 installed on a machine in my office. This Machine acts primarily as a router and gateway for the LAN behind it.
Iptables is configured with shorewall.

I also have a SBS Server running in the LAN with IIS, which works fine.
Thats why i mapped apache to the port 8082.

Now when i try to access that apache via example.dyndns.org:8082 it tells
me:

Not Found

The requested URL / was not found on this server.
Apache/2.2.9 (Ubuntu) Server at xx.xx.xx.xx Port 8082

I wonder why that is. It can access the apache, but not the standard "It work's" Site.

Any Ideas?


Thanks in Advance
Sven

---

### Post by superprash2003 on 2009-01-19
have you port forwarded port 8082 in your router?? do you have firestarter or anything similar running? use this online port scanner to see if 8082 is open or not . [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by sveri on 2009-01-19
Yes, like i said the apache host is the router.
And if i scan the host with nmap it shows that the port 8082 is opened.

---

### Post by superprash2003 on 2009-01-22
what does the online port scanner say??

---

### Post by AlexDudko on 2009-01-22
> **sveri said:**
> 
Not Found

The requested URL / was not found on this server.
Apache/2.2.9 (Ubuntu) Server at xx.xx.xx.xx Port 8082



If there is an answer from apache - it works, the problem could be in server's root directory and the availability of the index file there.
Check DocumentRoot directory in your apache2.conf and whether there is anything in that directory.

---


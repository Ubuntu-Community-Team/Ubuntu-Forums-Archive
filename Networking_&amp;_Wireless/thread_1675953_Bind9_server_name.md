---
title: "Bind9 server name"
date: 2011-01-26
forum: Networking &amp; Wireless
---

### Post by markbann on 2011-01-26
Noobie
Ubuntu 10.10 LTS
I could not access apache webserver with server name [http://myserver](http://myserver) from windows machines that had static IP's.  (Could see it with IP address)Machines were all pointed to openDNS for DNS service.    Server configured with a static IP.
I configured Bind9 (through webmin) only changing the DNS servers it look for.  
Adjusted DNS on windows machines to first look at the Ubuntu server.  That worked great.  
Made other unrelated changes and then occassionally would lose access to server with its name.  After a while (and some restarts) can't reach it by name at all.
I don't know anything much about Bind9.  
Where is the best place to start looking?
Any suggestions?

---


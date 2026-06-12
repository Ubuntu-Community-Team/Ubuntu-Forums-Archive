---
title: "How to open Port 80"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by marciab on 2011-03-22
I have Ubuntu 10.10 installed. When I do a port scan using the network tools Port 80 is not listed. I am trying to get our new SpiceWorks server to scan my Ubuntu machine and it keeps failing.
I have used this cmd:
$ sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
 but still don't see Port 80 listed in the port scan tool. We have 2 other Ubuntu computers that have an older version of Ubuntu and SpiceWorks can scan them. When I run the port scan on them Port 80 is listed.

Thanks,

Marcia

---


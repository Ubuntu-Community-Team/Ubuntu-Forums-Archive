---
title: "vsftpd (with ssl) not active"
date: 2012-01-30
forum: Networking &amp; Wireless
---

### Post by BuAziz on 2012-01-30
I am using Ubuntu desktop 11.10 and I've installed vsftpd. It works  perfectly until I add "ssl_enable=YES" to "/etc/vsftpd.conf". when I do so the demon will not open a port !!!:(

I used *nmap* to trace the port and it is closed

I have tried to change the port by adding "listen_port=" and it is the same problem. 

When I remove the ssl_enable line it will work and the port number at listen_port will be active.

I do restart the demon after every time I modify the vsftpd.conf by using the following command
[INDENT]*sudo /etc/init.d/vsftpd restart*[/INDENT]

how can I check the status of a service ? and
how can trace and solve this problem?

---


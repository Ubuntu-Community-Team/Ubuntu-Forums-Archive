---
title: "netstat local address column"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by jackycs on 2010-12-22
when i run 'sudo netstat -lptu', i get the following list.

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:mysql         *:*                     LISTEN      1218/mysqld     
tcp        0      0 *:ssh                   *:*                     LISTEN      1006/sshd       
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      1006/sshd
udp6       0      0 localhost:ntp           [::]:*                              2148/ntpd       
udp6       0      0 [::]:ntp                [::]:*                              2148/ntpd 

my question is, why the local addresses are in different format? sometimes it is *:ssh, sometimes it is [::]:ssh, sometimes its localhost:ssh? could you please tell what they mean or point me to the right docs?

Thanks a lot,
J

---


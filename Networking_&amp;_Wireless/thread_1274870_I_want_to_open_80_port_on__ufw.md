---
title: "I want to open 80 port on  ufw"
date: 2009-09-25
forum: Networking &amp; Wireless
---

### Post by csejo123@yahoo.com on 2009-09-25
[SIZE=3]****[/SIZE]dear sir
I am using mtnl ppp0 i want to open tcp port 80 from external or internet


i will give you the ufw status

root@ubuntu:~# ufw status
Status: active

To                         Action  From
--                         ------  ----
22                         ALLOW   Anywhere
8080                       ALLOW   Anywhere
3128                       ALLOW   Anywhere
Anywhere                   ALLOW   192.168.0.0
Anywhere                   ALLOW   59.181.0.0
Anywhere                   ALLOW   59.181.129.36
Anywhere                   ALLOW   10.100.100.1
Anywhere                   ALLOW   192.168.1.194
Anywhere                   ALLOW   0.0.0.0
Anywhere                   ALLOW   10.100.100.4
Anywhere                   ALLOW   10.100.100.0
Anywhere                   ALLOW   192.168.1.0
10.100.100.1               ALLOW   192.168.1.194
80/tcp                     ALLOW   59.181.129.36
25                         DENY    Anywhere
110                        DENY    Anywhere
80                         ALLOW   Anywhere
443                        ALLOW   Anywhere
Anywhere                   ALLOW   192.168.1.194 80
Anywhere                   ALLOW   0.0.0.0 80
80                         ALLOW   59.181.129.36



Thanks

Sejo

---


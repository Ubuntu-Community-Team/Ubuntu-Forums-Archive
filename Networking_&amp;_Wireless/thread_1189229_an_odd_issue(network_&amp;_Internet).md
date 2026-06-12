---
title: "an odd issue(network &amp; Internet)"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by Zylynghost on 2009-06-16
I have been running 8.10 server since its release.  I have just installed 9.04 desktop and i have no inter net connection. the terminal services does however.  People can get to my server but the gui cant get out.  this is odd enough for me to post since i can't resolve this my self.

i am a noob when programming so please post in a manner i can fix this issue.

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever


2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1492 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:12:3f:9e:b2:8e brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.100/24 brd 192.168.1.255 scope global eth0
    inet6 fe80::212:3fff:fe9e:b28e/64 scope link
       valid_lft forever preferred_lft forever


3: pan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN
    link/ether b2:23:20:42:3a:93 brd ff:ff:ff:ff:ff:ff


I believe its something t do with #3  but other then that no clue

---


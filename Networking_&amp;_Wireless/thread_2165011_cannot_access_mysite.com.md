---
title: "cannot access mysite.com"
date: 2013-08-02
forum: Networking &amp; Wireless
---

### Post by lfernandez60 on 2013-08-02
I cannot access mysite,com but I can access hostname.mysite.com
Using zenmap mysite.com will show all ports closed
And hostname.mysite.com will show 80 and others open
ubuntu 12.04
My host file is
127.0.0.1    localhost
127.0.1.1    archangelstv.localdomain localhost
192.168.0.8     archangelstv  archangelstv.archangelstv.com


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

### Post by TheFu on 2013-08-03
Use **dig** to see what DNS returns for hostname.mysite.com vs mysite.com - then correct your DNS settings.

---


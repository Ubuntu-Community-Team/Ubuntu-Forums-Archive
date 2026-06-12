---
title: "about pppoeconf connect"
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by tacoee on 2010-05-22
hi, every one, I got a problem about pppoeconf to connect ADSL now.
every time I have do below steps to make my ADSL work

1, sudo /etc/init.d/networking restart
2, sudo pppoeconf and enter user and password and all other options set "yes"

what happen on it? I remember pppoeconf can connect ADSL automatically. 

how to resolve this problem?

my /etc/network/interfaces file as below:
   
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider

auto eth1
iface eth1 inet manual

BTW, I use wicd to connect router.

---


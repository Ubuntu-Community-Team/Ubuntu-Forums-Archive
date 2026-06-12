---
title: "question about bind9, and multiple servers"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by meomike2000 on 2009-01-12
if i were to set up a machine and call it my gateway, gateway.domain.net. and install bind9 and set up my zone file with the entrys of all my servers, say s1.domain.net and s2.domain.net(both would be web serves). and i had 1 static ip address from my service provider of xxx.xxx.xxx.x. assigned to the machine gateway on eth0, and the other 2 machines s1 and s2 were on the internal network behind gateway connected to eht1 with an internal static ip address. would this work. or would the web servers also have to have public ip addresses.

---

### Post by meomike2000 on 2009-01-15
i have been given more info on this thanks to marpada over at howtoforge.com.


[http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server](http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server)

[http://www.debian-administration.org/articles/73](http://www.debian-administration.org/articles/73)

if others are having this same problem, i hope this helps...

mike.

i would mark as solved but the link is missing... sorry.

---


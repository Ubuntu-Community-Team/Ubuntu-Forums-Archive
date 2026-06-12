---
title: "limit speed of 2 IPs using iptables"
date: 2013-08-16
forum: Networking &amp; Wireless
---

### Post by atux on 2013-08-16
[FONT=Verdana]Hello everyone.I do have a VPS running services for me, such as:
-email server
-web server
-openvpn for remote connection
-ssh
 
the available speed is 10Mbps
up to now the system is protected by iptables and allows only the forementioned services and blocks the brute force attackers.
I have noticed that when i get connected through openvpn it consumes all the available traffic of the system, as far i am using it. So i would like to limit it down to 1Mbps maximum speed.
The VPS has a public IP such as 62.62.38.100 and the OPENVPN user when gets connected it has an IP from the range 10.0.8.0/24. The VPS has the 10.0.8.1/24 IP for the OPENVPN as a getway.
Is there a way to limit the speed of download/upload of the connected users through OPENVPN? 
 
 
John
[/FONT]

---

### Post by prodigy_ on 2013-08-16
Try these HOWTOs:
[http://www.szabilinux.hu/bandwidth/](http://www.szabilinux.hu/bandwidth/)
[http://www.cyberciti.biz/faq/iptables-connection-limits-howto/](http://www.cyberciti.biz/faq/iptables-connection-limits-howto/)

---

### Post by atux on 2013-08-20
i have seen these, prior to my post. my situation is different:
-it is not a router
-there is only one ethernet card

i have tried to create something
 tc qdisc add dev $DEV root handle 1: cbq avpkt 1000 bandwidth 10mbit 

      tc class add dev $DEV parent 1: classid 1:1 cbq rate 512kbit \
      allot 1500 prio 5 bounded isolated 

      tc filter add dev $DEV parent 1: protocol ip prio 16 u32 \
      match ip dst 10.0.8.2 flowid 1:1

but i do not know how to:
-make it work
-make it for more IPs (10 in total)

up to know my iptables is something like:
iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --sport 22 -m state --state ESTABLISHED -j ACCEPT

iptables -A INPUT -i eth0 -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT

---


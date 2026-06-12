---
title: "Ubuntu 10.04 + squid transparent proxy help"
date: 2011-03-27
forum: Networking &amp; Wireless
---

### Post by dysonsphere 99 on 2011-03-27
Hello  Im trying to configure a simple transparent proxy to no avail.

I have 10.04 up and running, with squid 2.7 and if I set the proxy in the browser settings everything works fine.

I am trying to set up a transparent proxy so that I dont have to go to each machine/user and setup proxy settings.

my configuration on the 10.04 box

eth0  external ip addr
eth1  internal ip addr

squid is currently using just default values
http_port 3128  transparent

acl localnet src 172.16.0.0/255.255.0.0
http_access allow localnet

my iptables include 
iptables -t nat -A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 172.166.0.1:3128
iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128

there is no other iptable rules or any kind of filtering

Ive gone over various squid transparent proxy mini-howtos, webpages, documentation...

the proxy works if I manually set each web browser  I want to redirect the web requests from my internal network to the proxy without having to set up each user's web browser(s) proxy settings

I'm probably just overlooking something but I just cant see where the problem is

---


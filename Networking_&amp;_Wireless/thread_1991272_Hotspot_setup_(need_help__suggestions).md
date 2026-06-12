---
title: "Hotspot setup (need help / suggestions)"
date: 2012-05-30
forum: Networking &amp; Wireless
---

### Post by domdurocher on 2012-05-30
Hello, First post on this forum has far as I can recall so bear with me ill try to be clear and precise. 

Due to specific need I have a gateway built on ubuntu 12.04 lts that connect to the internet and server the following purpose:

Firewall (iptable) 
DPCH (ISC-DHCP-SERVER)
DNS (bind) 
Webserver (apache + php)
Db server (mysql) 
and much more ... 


The physical layout looks like that: 


```

ISP ------- eth0 --- ubuntu ---- eth1 --- lan 
                         |
                         |  ---- wlan0 --wifi

```
I have a bunch of known device that connect on a dayly basis and I have some people that will connect to simply upload files to my server and do not need internet access. 

What I have in mind is to use iptable to allow access to the internet to the "known" devices using the host declaration in dhcp giving them a fixed address and allowing that block of ip to access the internet. 

Now for the "visitor", here's 2 question I have:

1: Should I simply let the dhcp give them and ip within a specific range and filter that in iptables? (shared-network, other subnet, I need detailed info on that part)

2: Is it possible to redirect those "visitor" to a webpage on my lan using iptables? (I'm pretty confident I can redirect to a specific ip but that wont send them to a specific webpage, is it possible to redirect to a url?) 

I've looked at chillispot and other wireless access point controler but due to some specification I cannot overcome I have to find another solution. 

Suggestion, solution, ideas are more than welcome. 

Regards 

Dominic

---


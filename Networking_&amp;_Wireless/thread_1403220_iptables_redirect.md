---
title: "iptables redirect"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by blackcloud on 2010-02-10
help me "i have webserver on my lan with ip 192.168.0.1 and this webserver behind firewall router 192.168.0.1 eth1 and 192.168.1.2 my connection use pppoe. my question how i can use this webserver be my public webserver so if i call my ip ex. 125.198.xx.xx then my webserver show not my router".

and for my second question "i cant access my yahoo mesenger with this iptables how i can solve this so i can access may yahoo mesenger and this is my iptables:
 
> oot@ngadmin:/var/log# iptables -L
Chain INPUT (policy DROP)
target prot opt source destination
ACCEPT all -- anywhere anywhere
ACCEPT all -- 192.168.0.0/24 anywhere
ACCEPT icmp -- ngadmini anywhere
ACCEPT all -- anywhere anywhere state RELATED,ESTABLISHED
ACCEPT tcp -- anywhere anywhere tcp dpt:3128
LOG all -- anywhere anywhere limit: avg 2/min burst 2 LOG level warning prefix `**INPUT DROP**'
LOG all -- anywhere anywhere limit: avg 2/min burst 2 LOG level warning prefix `**FORWARD DROP**'
LOG all -- anywhere anywhere limit: avg 2/min burst 2 LOG level warning prefix `**OUTPUT DROP**'
ACCEPT tcp -- ngadmini anywhere tcp dpt:mmcc
ACCEPT tcp -- ngadmini anywhere tcp dpt:5150

Chain FORWARD (policy DROP)
target prot opt source destination
ACCEPT tcp -- anywhere anywhere tcp dpts:5000:5001
ACCEPT tcp -- 192.168.0.0/24 anywhere tcp dpt:ftp
ACCEPT udp -- 192.168.0.0/24 anywhere udp dpt:fsp
ACCEPT tcp -- ngadmini anywhere tcp dpt:212
ACCEPT tcp -- 192.168.0.0/24 anywhere tcp dpt:mmcc
ACCEPT udp -- 192.168.0.0/24 anywhere udp dpt:mmcc
ACCEPT all -- anywhere anywhere state RELATED,ESTABLISHED
ACCEPT tcp -- anywhere anywhere tcp dpt:domain
ACCEPT udp -- anywhere anywhere udp dpt:domain
ACCEPT tcp -- 192.168.0.0/24 anywhere tcp dpt:www
ACCEPT tcp -- 192.168.0.0/24 anywhere tcp dpt:mmcc
ACCEPT tcp -- anywhere anywhere tcp dpt:www
ACCEPT tcp -- anywhere anywhere tcp dpt:smtp
ACCEPT tcp -- anywhere anywhere tcp dpt:pop3
ACCEPT tcp -- webserver anywhere tcp dpt:www
ACCEPT tcp -- webserver anywhere tcp dpt:smtp
ACCEPT tcp -- webserver anywhere tcp dpt:pop3
ACCEPT tcp -- ngadmini anywhere tcp dpt:mmcc
ACCEPT tcp -- ngadmini anywhere tcp dpt:8000
ACCEPT tcp -- ngadmini anywhere tcp dpt:5150
ACCEPT tcp -- ngadmini anywhere tcp dpt:1638
ACCEPT tcp -- ngadmini anywhere tcp dpt:5001
ACCEPT tcp -- anywhere anywhere tcp dpt:www

Chain OUTPUT (policy DROP)
target prot opt source destination
ACCEPT all -- anywhere anywhere
ACCEPT all -- anywhere anywhere state RELATED,ESTABLISHED
ACCEPT tcp -- anywhere anywhere tcp dpt:www
ACCEPT tcp -- anywhere anywhere tcp dpt:domain
ACCEPT udp -- anywhere anywhere udp dpt:domain
ACCEPT tcp -- ngadmini anywhere tcp dpt:mmcc
thanks before.

---

### Post by mtron on 2010-02-10
to make your webserver accessible for the world you need to setup port forwarding on the router.

Most routers come nowadays with a web-interface that makes this very easy ;) So what you need to do is get into the webinterface and look for something labeled "Port Forwarding" and configure it to forward traffic from port 80 to the IP of your server.

Also, check that you use static ip addresses in you local network!

---

### Post by blackcloud on 2010-02-10
and how about my yahoo mesenger port can you give me some, and thanks for webserver.

---

### Post by superprash2003 on 2010-02-10
you dont need to open any port on your router for yahoo messenger to work , what error are you facing?

---

### Post by blackcloud on 2010-02-11
my yahoo cant connect ant also if i open accept all input, output, forward i can connect but if i drop i cant connect whats wrong.
and about ip forwarder may i know the syntax of that iptables so i can forward port 80.

---

### Post by superprash2003 on 2010-02-17
is this webserver running server or desktop version of ubuntu?

---

### Post by blackcloud on 2010-02-17
this is ubuntu server

---


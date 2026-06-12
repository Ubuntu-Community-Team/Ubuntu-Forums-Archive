---
title: "iptables router - simple bridge help"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by alesserfate on 2009-11-15
hey fellow's

so i'm having a bit of a problem setting up a simple network with IPTABLES through terminal

here is the diagram, machine1 is the server, and machine two is a sample client, on different interface of the iptables router

it's a pretty basic example, linux IPTABLES machine in the center, one ethernet adapter faces towards the server, and the other one faces towards the client.


[machine1-serve]<--------->(eth0)[IPTABLES ROUTER](eth1)<------->[machine2]

(machine 1 services to go accross the router from eth0 to eth1)
HTTP:TCP:9090
DNS:TCP/UDP:53
IMAP:TCP/UDP:143
POP3:TCP:110
SMTP:TCP/UDP:25
FTP:TCP:21
MYSQL:3306
DHCP passthrough
DHCP server- passthrough to machine 2

(iptables router)
dhcp passthrough accross interfaces - broadcast traffic
block all other ports and services

There is no internet access involved in this setup. I've tried a few of my own strings but it doesn't work very well, any input would be greatly appreciated.

Thanks in advance.

---

### Post by alesserfate on 2009-11-18
anybody ?

---


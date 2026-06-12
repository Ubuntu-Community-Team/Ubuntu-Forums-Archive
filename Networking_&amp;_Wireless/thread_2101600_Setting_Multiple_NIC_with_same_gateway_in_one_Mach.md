---
title: "Setting Multiple NIC with same gateway in one Machine"
date: 2013-01-05
forum: Networking &amp; Wireless
---

### Post by davidyordan777 on 2013-01-05
hi guys,
a newbie network administrator here...
i have a PC, I want to use it as transparent proxy server
and also running one virtual machine as MySQL server,
I'm using 3 network cards,

eth0 is used to connect the server to my router (WAN) (IP 192.168.0.2)
eth1 is used as gateway to share internet connection to my network (IP 192.168.1.1)
and last  can i use eth2 (192.168.1.2) as bridged NIC to my virtual machine, so
the eth2 will have the same gateway as eth1..

before I set the eth2, the proxy was working fine, i can connect to internet using client computer.
but when i try set up eth2 at the same gateway as eth1, the client computer fail to connect to the internet..
can someone help me,, is there something wrong?? i was set interface manually at the /etc/network/interfaces, but client still cant connect to internet..
how to set up third (eth2) NIC at the same gateway ??

this is my topology :
eth0 IP 192.168.0.2 connected to router
eth1 IP 192.168.1.1 as gateway to share internet connection, connected to LAN Hub.
i want to set eth2 IP 192.168.1.2 as bridged interface for my Virtual Machine,

can somebody help me ?
sorry for bad english..
thx you for your reply

---

### Post by dereklai on 2013-01-30
You should post the output of your route command and ifconfig -a to make it easy for people to help you.

---

### Post by BlinkinCat on 2013-01-30
> **dereklai said:**
> You should post the output of your route command and ifconfig -a to make it easy for people to help you.

Plus bump your thread each 24 hours rather than waiting this long.

Cheers - :p

---

### Post by dereklai on 2013-05-14
I take it bumping my thread means to somehow raise the visibility in the hope of having it answered sooner? How does one bump his own thread?


Thanks,

Derek

---


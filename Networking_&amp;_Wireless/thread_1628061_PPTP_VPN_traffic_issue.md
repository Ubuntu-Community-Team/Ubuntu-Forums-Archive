---
title: "PPTP VPN traffic issue"
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by oturpin on 2010-11-22
Hello,

I am trying to configure PPTP VPN to an enterprise network but cannot achieve making it run correctly.
My networking knowledge are weak and I need help to fix my configuration. If you could propose any solution, many thanks to you.

My local network is 192.168.1.0/24.
My distant network is 192.168.0.1/24. I have a DDWRT router running and serving PPTP with 192.168.0.1 as host address.

Routes before VPN connection are the following:

Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         livebox.home    0.0.0.0         UG    0      0        0 wlan0

I configured a VPN on local workstation with public IP, login and password. 
The connection to PPTP server is done with no error.

Routing table becomes:

Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
192.168.0.1     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
82.126.104.118  192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
82.126.104.118  192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

82.126.104.118 is the public IP of distant DDWRT router (and PPTP server)

Problem is that distant network cannot be reached.
When I try to ping distant network, I get partial traffic go through.
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=84.8 ms
64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=90.7 ms
64 bytes from 192.168.0.1: icmp_req=5 ttl=64 time=86.7 ms
64 bytes from 192.168.0.1: icmp_req=8 ttl=64 time=165 ms
64 bytes from 192.168.0.1: icmp_req=11 ttl=64 time=85.8 ms
64 bytes from 192.168.0.1: icmp_req=14 ttl=64 time=88.9 ms
64 bytes from 192.168.0.1: icmp_req=17 ttl=64 time=85.8 ms
64 bytes from 192.168.0.1: icmp_req=20 ttl=64 time=89.0 ms
64 bytes from 192.168.0.1: icmp_req=23 ttl=64 time=86.8 ms

After packet number 23, nothing will go through.

May you have some idea about this issue ?

Thx for your help !

---


---
title: "routing multicast with two NICs"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by MonteZ on 2010-08-20
HI
I've been trying unsuccessfully to set up static route on my system with two NIC cards, so i hope someone here can give me a hand...

This is my setup:
eth0 > adsl modem/router > port only for IpTV
wlan0 > adsl modem/router > internet

This router has two networks
192.168.1.0 /24  > my local home network
10.100.152.0 /21 > for IPTV

My routing table looks like:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
10.100.152.0    *               255.255.248.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
default         10.100.152.1    0.0.0.0         UG    100    0        0 eth0

Depends on which network i join first that would be my default and that creates a problem cause sometimes i can't go on internet and sometimes i can not watch tv.

I use VLC to watch TV, with the playlist with all channels, for exmple udp://@224.10.xx.xx:1234 and different IP addresses for different channels.

I tried adding static route for 224.0.0.0/4 on eth0 so the multicast traffic would be received from that interface instead the wlan0 interface.
Also wlan interface has to be a default one, and not like on the routing table above where i have two default gateways.

So the question is ....
How do i accomplish to go to internet trough wlan0 and receive multicast traffic trough eth0.

I hope this is not that hard....
PLease help
Thank You

---


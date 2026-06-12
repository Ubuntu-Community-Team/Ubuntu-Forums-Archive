---
title: "Dual NIC's and ADSL modem in Bridge mode"
date: 2013-01-15
forum: Networking &amp; Wireless
---

### Post by stomp! on 2013-01-15
Hi,

Having general problems with my Ubuntu 12.04 server.

Have dual network cards that are setup as such:
```

auto lo
iface lo inet loopback

#interface to our WAN / ADSL Modem in Bridge
auto eth0
iface eth0 inet static[INDENT]address xxx.yyy.113.138
netmask 255.255.255.0
network xxxx.yyy.113.0
gateway xxx.yyy.113.254
broadcast xxx.yyy.113.255
dns-nameservers aaa.bb.160.35
[/INDENT]#interface to our LAN
auto eth1
iface eth1 inet static[INDENT]address 192.168.1.222
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
[/INDENT]
```
My primary issue is that I can access the internet from the server, but from any (windows) machine connected to the LAN if I use 192.168.1.222 as the DNS server I can't get DNS, but if I use aaa.bb.160.35 I can.

I am using UFW. 

Any suggestions on what I can can do about the LAN clients setting 192.168.1.222 as the DNS and somehow having this work through Ubuntu and UFW?

Thanks
Stomp

---


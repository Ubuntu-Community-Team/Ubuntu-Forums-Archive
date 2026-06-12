---
title: "Static IP - cannot connect to Ubuntu or ping it from outside"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by kinglear333 on 2009-12-13
Hello everyone,

This is my first post and I would like to first say that I fell in love with Ubuntu! Not just Ubuntu but Linux in general. There is so much to learn I don't know where to start!

With that said...

I installed Ubuntu Server on a brand new IBM IdeaCentre. This is what I added to server:

[LIST]
[*]SSH - selected during installation, afterwards secured it with no direct root login, disabled X11 forwarding.
[*]Apache2 - installed via apt-get
[/LIST]
This server worked fine when connected to router with DHCP. However, when I moved it to its own static IP, I could not ping the box anymore.

I configured the network in /etc/network/interfaces, set proper DNS servers, restarted networking service, etc. but still no luck. I can, however, ping other sites from the box (strange!)

This is my /etc/network/interfaces:
```
auto eth0
iface eth0 inet static
address 96.xx.xxx.4
netmask 255.255.255.248
network 96.xx.xxx.1
gateway 96.xx.xxx.1
broadcast 96.xx.xxx.7
```I flushed the IPTABLES and there's nothing in terms of firewalls blocking access to the box. No hardware firewall either. When I was connected through a router, I was able to connect to the server from LAN as well as externally (router port forwarding).

Can someone please help me troubleshoot this? :(

Thank you!

-KL

---

### Post by kinglear333 on 2009-12-13
Figured out the problem. In my case it was the Cisco router provided by my ISP that was dropping all intra-network traffic (from 1 Static IP to another) so I could not ping or connect to my Ubuntu Server from my other IP. However, others from different places could ping and connect to my Ubuntu Server fine.

Thank you to all the people in the #ubuntu-server chatroom!

---


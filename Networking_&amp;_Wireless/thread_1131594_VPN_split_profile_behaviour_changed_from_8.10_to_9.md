---
title: "VPN split profile behaviour changed from 8.10 to 9.04?"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by stephanhughson on 2009-04-21
Hi,

I use Ubuntu to connect to my work's Cisco ASA VPN connection. We have set it up so that anything that needs to go to work goes down the VPN and anything that doesn't (e.g. public Internet) just goes straight to its destination. I think it's called a "split profile" or "split tunnel".

In 8.10, this just worked automatically, but in 9.04, I had to go to the network manager page, then goto the VPN tab, edit my connection, IPv4 settings, Routes, then tick "Use this connection only for resources on its network".

Then in route -n, I get 

0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

whereas previously it was sending everything down "tun0" (the VPN link). 192.168.1.1 is my home router by the way.

dpkg --list|grep vpnc
ii  network-manager-vpnc                       0.7.1~rc4.20090316+bzr21-0ubuntu2       network management framework (VPNC plugin)
ii  vpnc                                       0.5.3-1                                 Cisco-compatible VPN client

I think the default behaviour has changed since 8.10, so I'm mentioning this in case it's a bug, or in case it helps anyone work out the issue faster than I did.

---


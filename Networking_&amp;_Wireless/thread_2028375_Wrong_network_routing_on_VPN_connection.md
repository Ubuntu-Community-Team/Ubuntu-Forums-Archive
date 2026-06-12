---
title: "Wrong network routing on VPN connection"
date: 2012-07-18
forum: Networking &amp; Wireless
---

### Post by yedidel on 2012-07-18
Hello,
I am using Forticlient SSLVPN to connect to my office.

After I make the connection, I have no internet connection or connection to my office network because my routing table looks like this:

0.0.0.0         10.212.114.100  0.0.0.0         UG    0      0        0 ppp0
0.0.0.0         192.168.5.1     0.0.0.0         UG    0      0        0 wlan0
81.218.149.127  192.168.5.1     255.255.255.255 UGH   0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.5.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

and then I need to run the following two commands to make it work:


sudo route del -net 0.0.0.0 ppp0
sudo route add -net 192.168.1.0 netmask 255.255.255.0 ppp0

How do I make it happen automatically? I tried putting it in /etc/network/interfaces but all network doesn't work because ppp0 doesn't exist on boot.

---


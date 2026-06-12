---
title: "Internet sharing. Windows/Ubuntu"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by EvolLove on 2010-01-15
Hello

I faced with a problem when I tried to set an internet sharing. I would be thahkful if You help me.

I have:
ADSL modem Zyxel (with activated Routing mode)
Computer1 (with installed Ubuntu 9.10/Windows Xp) - interface Auto eth1
Computer2 (with installed Windows Xp) - interface Auto eth0

Computer1 looks into the internet. Computer2 is connected to computer1 through the computer1's second netcard.

Under windows both computers have the internet. Computer2 detects net configuration automatically.
Under Ubuntu computer2 can't do it.

What did I do?
1) I opened file /etc/sysctl.conf and uncommented net.ipv4.ip_forward = 1
2) Set the following Auto eth0's settings:
ip 192.168.0.1
subnet mask 255.255.255.0
3) I executed
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
echo "1" >/proc/sys/net/ipv4/ip_forward

Computer2 hasn't interner. What did I do wrong?

Ifconfig and route are here:
[[IMG]http://savepic.org/173138m.png[/IMG]](http://savepic.org/173138.htm)

---


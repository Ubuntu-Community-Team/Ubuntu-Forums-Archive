---
title: "help to setup ubuntu as a router"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by stenrul on 2009-01-14
Hi, does any one know any software/code that will allow me to setup ubuntu as a router. The router software/code will need to do:
-share the internet connection
-allow all ports
-able to limit speed if needed at the time
-works with 2 networks cards e.g. eth0 (internet) eth1 (local)
-works with dhcp (on eth0 (client of dhcp) and eth1 (dhcp server to share with the rest of the local pc/ servers)

If any one know how to setup this please tell me.
Thanks

---

### Post by stenrul on 2009-01-14
If any one does know please tell me. Even if you are typing a how to up or something on it. I would like to know if someone is typing something up for it. Thanks a lot

---

### Post by Iowan on 2009-01-14
I don't have the whole package, but [here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is the first part...

---

### Post by stenrul on 2009-01-14
OK, thanks. Does any one know how to limit the speed and monitor how much is getting used? e.g. 258mb day 1. Please tell me if any does know.

---

### Post by stenrul on 2009-01-14
Hi, would someone be able to create a script that setups ubuntu as a router?
using these commands "https://help.ubuntu.com/community/Internet/ConnectionSharing"
With DHCP server, etc. Have input for internet network card name and local network card name. Also, have input for dhcp range. If any one can find/create this script please tell me.
thanks

---

### Post by stenrul on 2009-01-15
Hi, i have tried to get this to work. I did this 100% to the how to. my eth0 was the internet line and the eth1 was the local. Could someone please try it and tell me if they have the same problem . If any could create a script that does work, please tell me. the problem is that i can ping 192.168.0.1 but can not ping [www.google.com](www.google.com)

> Configure internal network card

Configure your internal network card (eth1) for static IP like so:

sudo ifconfig eth1 192.168.0.1

(The external and internal network cards cannot be on the same subnet)
Configure NAT

Configure iptables for NAT translation so packets can be correctly routed through the Ubuntu gateway.

sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE 

(rule1 allows forwarded packets (initial ones), rule2 allows forwarding of established connection packets (and those related to ones that started), rule3 does the NAT.)

Enable routing

    * Configure the gateway for routing between two interfaces by enabling IP forwarding: 

sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

    * Edit /etc/sysctl.conf and add these lines: 

net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1



---


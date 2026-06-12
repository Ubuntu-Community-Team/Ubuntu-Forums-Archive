---
title: "Routing between pptp,l2tp and openvpn"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by Gaku on 2011-02-03
Hello!
On my ubuntu server installed xl2tpd (192.168.2.x), pptpd (192.168.3.x) and OpenVpn (192.168.4.x).

1. I'm connecting to the network by iPhone through PPTP.
2. Router (with home network 192.168.1.x) through OpenVpn

OpenVPN (ubunut's server), server.conf:
> dev tun0
port 3333
proto udp
ifconfig 192.168.4.1 192.168.4.2
secret /etc/openvpn/keys/static.key
user nobody
script-security 2
push "route 192.168.1.0 255.255.255.0"
push "route 192.168.2.0 255.255.255.0"
push "route 192.168.3.0 255.255.255.0"
persist-tun
persist-key
verb 3
log-append /var/log/openvpn.log
keepalive 10 60


but I cannot ping from my iphone (192.168.3.2) home network 192.168.1.x :-(

What can I do, to be able get access to iPhone from homenetwork?

---


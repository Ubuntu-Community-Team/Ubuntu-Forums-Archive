---
title: "multiple routing table and vpn"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by Kamikase on 2010-03-22
Hi everybody,

First (interesting?) message :

My config:
eth0: 192.168.1.6 (gw 192.168.1.1)
tun0: 10.0.0.1 (gw 10.0.0.254) --> VPN

I want to configure my VPN with multiple routing tables.

First, I add a rule to send all packets with TOS = 0x14 to another table :
ip rule add tos 0x14 table 8

Then, I add a route in this table
ip route add default via 10.0.0.254 dev tun0 table 8

Then, if I do:
ping [www.ubuntu.com]("http://www.ubuntu.com") -Q 0x14

I see the echo request/reply on tun0 but my ping command does'nt work (100% loss).

Any Idea?

---


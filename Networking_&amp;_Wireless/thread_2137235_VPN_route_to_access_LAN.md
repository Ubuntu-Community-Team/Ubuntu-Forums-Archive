---
title: "VPN route to access LAN"
date: 2013-04-20
forum: Networking &amp; Wireless
---

### Post by joeherold on 2013-04-20
Hello!

I have a short question about pptpd VPN server settings:

I have a router (Draytek Vigor) with an ip of 192.168.26.1
I have an Ubuntu Server with an ip of 192.168.26.25 connected to the router.
The Server is a 12.0.4 LTS machine on a DELL poweredge hardware.

Clients connect via VPN to the Ubuntu Server an get an ip-range of 192.168.2.2-100 assigned.
The server is reachable via 192.168.2.1 and 192.168.26.25

Shares of the Server are reachable as well, but...
my problem now is, that I can not access other clients/ressources of the 192.168.26.0 pool, for example 192.168.26.13

On the VPN-client I set up to run all traffic over vpn connection...

How do I have to set everything up on the server side? (iptables and routes)

Pleas, help me! THX

---

### Post by Adity Iyer on 2013-04-25
hey i wanted to setup a vpn conection can u help me

---


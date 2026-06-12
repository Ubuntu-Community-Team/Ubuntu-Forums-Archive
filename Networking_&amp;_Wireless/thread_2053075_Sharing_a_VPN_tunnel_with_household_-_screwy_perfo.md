---
title: "Sharing a VPN tunnel with household - screwy performance"
date: 2012-09-04
forum: Networking &amp; Wireless
---

### Post by serveboy1 on 2012-09-04
Hello,

So at school we have to use Cisco AnyConnect VPN software to access the internet.

What I did was create an ad-hoc network and used the computer with the VPN connection to NAT all connections. So only one computer is aware of AnyConnect. All the others computers see a plain old wifi connection. The computer with the VPN connection has two physical devies: eth1 and wlan0. wlan0 connects to the network and then I create a tunnel tun0. eth1 connects to the home ad-hoc network.

It sort of works, but is very, very screwy. Everything works well on the the computer with the VPN connection. 

On the computers that are connected to the Wifi network, Skype works. Browsing works on SOME websites. Google works. But some websites don't. I thought it might be the DNS but I ran a dig and it's resolving IPs without any problems. IMAP works.  

Really lost on this one. Thanks for your help.

---


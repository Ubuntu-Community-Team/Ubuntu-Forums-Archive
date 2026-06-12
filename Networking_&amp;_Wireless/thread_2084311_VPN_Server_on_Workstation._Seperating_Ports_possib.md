---
title: "VPN Server on Workstation. Seperating Ports possible?"
date: 2012-11-15
forum: Networking &amp; Wireless
---

### Post by winniwinter on 2012-11-15
Hi,
on my workstation I'm using openvpn client for private surfing. 
When I'm away I want to access some services which are only locally available on my workstation. 
Therefore I wanted to install a ssh server on my workstation to securly connect to my network. 

The problem is, that at the moment all the traffic is going through the vpn tunnel which means also port 22 for ssh is populated through vpn.

What I want is to connect directly to my workstation:
client -> Workstation

Is it possible to add some kind of route in iptables for this port or configurate openvpn so this port is not forwared over the vpn?

---

### Post by winniwinter on 2012-11-15
I think I found my solution here: [https://bbs.archlinux.org/viewtopic.php?id=151870](https://bbs.archlinux.org/viewtopic.php?id=151870)

---


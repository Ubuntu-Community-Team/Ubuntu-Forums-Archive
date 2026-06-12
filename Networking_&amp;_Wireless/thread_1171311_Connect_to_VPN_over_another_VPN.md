---
title: "Connect to VPN over another VPN?"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by silanea on 2009-05-27
Hallo!

I have set up an OpenVPN server on my home gateway which I want to connect my laptop to over the internet. At university I am forced to connect the laptop to an IPSEC VPN to get internet access. Is it possible to "tunnel" my personal VPN connection through this university VPN? I am aware of the  overhead doing so will incur, it is of little concern to me.

My gateway runs Debian Lenny. It is reachable via a dynamic dns hostname. The services it provides and which I would like to gain access to are:
[LIST]
[*]Samba
[*]DHCP
[*]BIND
[/LIST]
The OpenVPN on it is set up as a tcp-based bridging network.

My laptop runs Ubuntu Jaunty. The IPSEC VPN is managed through network-manager.

Thank you very much,

silanea

---


---
title: "How do i setup a new VPN on 12.10 server?"
date: 2013-01-03
forum: Networking &amp; Wireless
---

### Post by vv1984 on 2013-01-03
Hi, 
i need to know the basic steps to setup a new VPN server on my Ubuntu 12.10 server. 
So that i can connect to my server from outside my home.

Thank you in advance.

---

### Post by Hadaka on 2013-01-03
Hi, this looks like a good possibility.

[http://www.thornstrom.net/how-to/linux/vpn-on-ubuntu-12/](http://www.thornstrom.net/how-to/linux/vpn-on-ubuntu-12/)

---

### Post by vv1984 on 2013-01-05
> **Hadaka said:**
> Hi, this looks like a good possibility.

[http://www.thornstrom.net/how-to/linux/vpn-on-ubuntu-12/](http://www.thornstrom.net/how-to/linux/vpn-on-ubuntu-12/)

Sorry, but this doesnt answer my question.

I nedd to setup a *brand new* vpn on my server.
So that i can connect to it from a client outside my home-network.

---

### Post by Rocklobster690 on 2013-01-05
It depends on your needs as there's a few options to consider:  
 
*OpenVPN Access Server - [http://openvpn.net/](http://openvpn.net/) 
Cisco Router - LT2P over IPSEC or PPTP 
Software based - [https://secure.logmein.com/UK/products/hamachi/](https://secure.logmein.com/UK/products/hamachi/) 
SSH Port Tunnelling - [http://ubuntuforums.org/showthread.php?p=12437917#post12437917](http://ubuntuforums.org/showthread.php?p=12437917#post12437917)  

Do you need to encrypt the data? Should your client require access to only one server or all servers on the network?

*I'd suggest starting here: [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)
or search OpenVPN [http://askubuntu.com](http://askubuntu.com) for tutorials.

Reply to the thread if you have any problems and I'll try to help.

Client setup - [https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)

You will also need to configure firewalls to allow the VPN protocol and setup Port Forwarding or NAT.

---

### Post by ahallubuntu on 2013-01-05
I use OpenVPN.  I have set it up on a couple of Ubuntu servers.  You can find How-Tos.  You can also setup OpenVPN on your router if you can install DD-WRT on it (if it's the full size DD-WRT that supports OpenVPN).  That way, you don't have to leave the server on 24/7 but your router probably is on anyway.

---

### Post by prsreek on 2013-07-02
given below is my VPS Specs.
50GB SATA3 RAID10 Storage
2GB Dedicated DDR3 RAM
4 vCPU Cores @3.4Ghz
1TB Premium Bandwidth @1Gbps
1 IPv4 Address

can i sell VPN configured in this server..?

---


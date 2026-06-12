---
title: "Unable to access my server outside from my local network"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by thierrydollar on 2013-01-07
Hi,

I have installed Ubuntu 12.04 on a server with the IP 192.168.1.2 running Apache.
I have chosen a TCP port number 81.
I have also installed sshd

With another PC on the same network I can access both Apache and sshd.

I have a router that connects a 192.168.0.x network to my 192.168.1.x network.

I have defined a NAT rule so that when I'm in the 192.168.0
network, I could access my server. Unfortunately this doesn't work. Neither Apache nor SSH.

I quite sure that my NAT rule is correct because I have other PCs on the 192.168.1.x network with several servers (VNC, FTP,...) and I can reach them from the 192.168.0.x network. 

I don't think that the problem is the Apache configuration (I have "allow from all", and I see no error message in the error.log).
I think that the problem is perhaps of firewall inside Ubuntu. ufw is disabled (ufw status => disabled)

Thanks for you help

Thierry

---


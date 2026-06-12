---
title: "Help getting on internet"
date: 2011-12-27
forum: Networking &amp; Wireless
---

### Post by chaseshaw on 2011-12-27
Ubuntu 11.04 very strange problems with internet. We moved so I redid my network from 192.168.1 to 192.168.10, and since then I cannot go on the internet.

HOWEVER, the machine is responding to ping, apache is up, and it accepts inbound connections like nomachine. Furthermore, if I type in the router's IP into firefox, the page comes up. Also typing in google's IP into ping doesn't work. Somehow outbound connections past my router aren't working. Is there a setting for this?

help!

thanks.

---

### Post by dandnsmith on 2011-12-27
Are you using DHCP, with the router allocating addresses?
What are you using as DNS reference source?
What do your routing tables look like?

---

### Post by collisionystm on 2011-12-27
First you need to know what your networking settings should be

Please list the following parameters

IP 192.168.1.10
Subnet /24
DNS ?
Gateway ?
Netbios ?

post output of 

cat /etc/resolv.conf

output of 

sudo route

output of 

cat /etc/hosts

output of

sudo iptables-save

---

### Post by chaseshaw on 2012-01-01
> **collisionystm said:**
> First you need to know what your networking settings should be

Please list the following parameters

IP 192.168.1.10
Subnet /24
DNS ?
Gateway ?
Netbios ?

post output of 

cat /etc/resolv.conf

output of 

sudo route

output of 

cat /etc/hosts

output of

sudo iptables-save

thanks this led me to it!

When we moved I changed my internal network to 192.168.10.1, and this conflicted with an old openvpn bridge.

---


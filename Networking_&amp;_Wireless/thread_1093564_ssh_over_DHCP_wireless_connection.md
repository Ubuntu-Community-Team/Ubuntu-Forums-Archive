---
title: "ssh over DHCP wireless connection"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by pjkiley on 2009-03-11
Hi all,

I am having trouble connecting via ssh.  I am trying to connect from my home laptop running ubuntu to a work desktop running suse (called XYZ here).  I get the error "ssh: connect to host XYZ port 22: No route to host"

However, I can ssh from an XP laptop using putty to XYZ, so I don't think its a firewall, and I also looked at /etc/hosts.deny on XYZ and that looks fine too.

I can ping, for example, [www.google.com](www.google.com) and resolve names, and use wget, so I don't think its a DNS problem either.  However, I cannot ping XYZ.

Also, I can ssh from my home laptop to other computers around the globe no problem!!  I am new to linux networking so it would be great if anyone could help as I am stumped.

Here is my IP routing table

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
131.xxx.xxx.xx  *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth1
default         route-cent-3.ca 0.0.0.0         UG    100    0        0 eth0


Any help would be fantastic!

cheers

---


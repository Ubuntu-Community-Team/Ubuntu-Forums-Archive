---
title: "UFW and VPN"
date: 2013-05-04
forum: Networking &amp; Wireless
---

### Post by tellme on 2013-05-04
Hello,

most of the time i solve my ubuntu problems by searching and reading however now i am real stuck for a week.
mail\ftp\www\rds\webmin\ssh portforwarding all works except VPN
I have a virual environment with ubuntu as firewall\gateway. Behind i have a windows domain controller server with dhcp and vpn configured.

[EMAIL="root@HG-GATEWAY"]root@HG-GATEWAY[/EMAIL]:~# ufw version
ufw 0.31.1-1
Copyright 2008-2010 Canonical Ltd.

I have made the following config with webmin for portforwarding:
-A PREROUTING -p tcp -m tcp -i eth0 --dport 1723 -j DNAT --to-destination 192.168.1.10:1723

I have added these 2 line in the before.rules:
-A ufw-before-input -p 47 -j ACCEPT
-A ufw-before-output -p 47 -j ACCEPT

outside ip port is 10.10.10.10 --> eth0
inside network is 192.168.1.0/24 --> eth2


I am strugling a week now to get this working.
Intern network virtual machines can connect to the vpn server.

This is what ufw logging says:
May  5 03:09:44 HG-GATEWAY kernel: [21503.274226] [UFW BLOCK] IN=eth0 OUT= MAC=00:15:5d:00:c9:21:00:d0:03:1e:10:00:08:00 SRC=195.241.XXX.XXX DST=85.17.XXX.XXX LEN=556 TOS=0x00 PREC=0x00 TTL=123 ID=18144 PROTO=UDP SPT=500 DPT=500 LEN=536 
 
May  5 03:09:46 HG-GATEWAY kernel: [21505.302020] [UFW BLOCK] IN=eth0 OUT= MAC=00:15:5d:00:c9:21:00:d0:03:1e:10:00:08:00 SRC=195.241.XXX.XXX DST=85.17.XXX.XXX LEN=556 TOS=0x00 PREC=0x00 TTL=123 ID=18145 PROTO=UDP SPT=500 DPT=500 LEN=536


someone can point me in the right direction,your input is realy appreciated ?

Tellme

---

### Post by wildmanne39 on 2013-05-04
Moved to own thread!

If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---


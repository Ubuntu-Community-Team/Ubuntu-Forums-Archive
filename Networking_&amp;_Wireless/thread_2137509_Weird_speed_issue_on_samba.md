---
title: "Weird speed issue on samba"
date: 2013-04-21
forum: Networking &amp; Wireless
---

### Post by spacecakes on 2013-04-21
Hi, i have ubuntu 12.04 installed on my server with a mdadm software raid 5 and i get some weird speeds over samba (ubuntu->win7), often speeds are around 55-60mb/sec but every once in a great while i get no lower than 95mb/sec, any ides?

ubuntu 12.04 with  3.8.0-030800-generic #201302181935 SMP Tue Feb 19 00:36:19 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux and samba 3.6.3 
smb.conf 
[global]
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536
name resolve order = lmhosts bcast host
printing = bsd


[accounts]
path = /home/assdick/raid
valid users = assdick
public = no
writable = yes

---


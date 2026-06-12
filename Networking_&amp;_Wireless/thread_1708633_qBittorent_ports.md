---
title: "qBittorent ports"
date: 2011-03-16
forum: Networking &amp; Wireless
---

### Post by adduds on 2011-03-16
is there still a bug in qBittorent with portforwarding 6881?

i forwarded it in my router and run nmap on localhost and shows its open yet it is always saying no direct connections on the bottom with that little yellow globe near the nodes

> toews@kidlapp:~$ nmap localhost

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2011-03-16 21:55 CDT
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00021s latency).
Hostname localhost resolves to 2 IPs. Only scanned 127.0.0.1
rDNS record for 127.0.0.1: localhost.localdomain
Not shown: 997 clolimitedsed ports
PORT     STATE SERVICE
22/tcp   open  ssh
631/tcp  open  ipp
6881/tcp open  bittorrent-tracker


---

### Post by adduds on 2011-03-17
oh and btw i can still d/l but i THINK it's probably going slower than it should...

---


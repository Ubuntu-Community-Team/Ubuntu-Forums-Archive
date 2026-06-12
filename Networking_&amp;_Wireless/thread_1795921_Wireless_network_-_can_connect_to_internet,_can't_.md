---
title: "Wireless network - can connect to internet, can't connect to other PCs (sometimes)"
date: 2011-07-03
forum: Networking &amp; Wireless
---

### Post by smcg on 2011-07-03
Hi

This might be Ubuntu, or might be my router - it's hard to tell.

I have two computers on 10.04 LTS, one server and one desktop. Both are connected by wireless to my router and have static IPs (desktop: 192.168.1.12, server: 192.168.1.110). They can always access the internet through my cable connection, however they occasionally seem to 'lose sight' of each other. That is, I can't ping one from the other, SSH, or access any of the services on the server.

Because they are both able to access the internet, I am working around this by opening a port on the router to allow me to SSH to the server via a domain name pointing at it, but obviously that's not ideal.

When I ping I just get the following:
```
user@server:~$ ping -c 5 192.168.1.12
PING 192.168.1.12 (192.168.1.12) 56(84) bytes of data.
From 192.168.1.110 icmp_seq=2 Destination Host Unreachable
From 192.168.1.110 icmp_seq=3 Destination Host Unreachable
From 192.168.1.110 icmp_seq=4 Destination Host Unreachable
From 192.168.1.110 icmp_seq=5 Destination Host Unreachable

--- 192.168.1.12 ping statistics ---
5 packets transmitted, 0 received, +4 errors, 100% packet loss, time 4008ms
, pipe 3
```

And, the other way:
```
user@desktop:~$ ping -c 5 192.168.1.110
PING 192.168.1.110 (192.168.1.110) 56(84) bytes of data.
From 192.168.1.12 icmp_seq=1 Destination Host Unreachable
From 192.168.1.12 icmp_seq=2 Destination Host Unreachable
From 192.168.1.12 icmp_seq=3 Destination Host Unreachable
From 192.168.1.12 icmp_seq=4 Destination Host Unreachable
From 192.168.1.12 icmp_seq=5 Destination Host Unreachable

--- 192.168.1.110 ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4025ms
, pipe 3
```

The router's Connected Devices Summary lists both with their correct IP and MAC addresses, and they also show in its ARP table. Any ideas what would cause this? Is there a conflict somewhere?

Thanks!

---


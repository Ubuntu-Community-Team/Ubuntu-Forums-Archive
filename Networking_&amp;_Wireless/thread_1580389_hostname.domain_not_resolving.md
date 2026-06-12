---
title: "hostname.domain not resolving"
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by rojmab on 2010-09-23
Hello,
I'm experiencing a weird DNS issues. Running 10.04LTS Server.

I CAN ping hostname, and it resolves properly from my MS DNS servers and reports back as hostname.mydomain.local.
however,
I CANNOT ping hostname.mydomain.local, the DNS just times out.

My etc/resolv.conf file:
domain mydomain.local
search mydomain.local
nameserver 192.168.59.155
nameserver 192.168.102.131

Both DNS servers are Microsoft domain controllers w/DNS. One is Server 2003, other Server 2008. All other windows hosts are able to resolve DNS properly, so it seems isolated to my linux box. 
It has the same behavior with or without the domain line. Also, the same with or without the search line.
Any thoughts???

root@netmonitor-ln:/var/log/samba# ping ithq80
PING ithq80.mydomain.local (192.168.110.80) 56(84) bytes of data.
64 bytes from ithq80.mydomain.local (192.168.110.80): icmp_seq=1 ttl=128 time=0.282 ms
^C
--- ithq80.mydomain.local ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.282/0.282/0.282/0.000 ms
root@netmonitor-ln:/var/log/samba# ping ithq80.mydomain.local
ping: unknown host ithq80.mydomain.local
root@netmonitor-ln:/var/log/samba#

---


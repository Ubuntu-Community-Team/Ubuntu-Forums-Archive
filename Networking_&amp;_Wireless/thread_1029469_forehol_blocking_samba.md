---
title: "forehol blocking samba?"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by AlistairHastings on 2009-01-03
Hey all,

I'm attempting to get firehol, tinyproxy, and dansguardian configured on my laptop.  With all three running, it appears to be blocking undesirable web traffic correctly.  However, firehol also appears to be blocking samba - nautilus no longer shows the Windows workgroup or shares.  However, the shares are accessible directly by IP address (smb://192.168.0.xxx).

If I stop dansguardian and tinyproxy, leaving only firehol running, the shares are still gone.  Stop firehol and the shares reappear immediately. So I think the problem is in the firewall.  

Here is my firehol.conf:
> version 5
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

transparent_squid 8080 "root root"

interface any world

protection strong

server samba	accept
server ICMP	accept
server cups	accept
server dns	accept
server microsoft_ds accept
server ntp 	accept
server ssh	accept

client all	accept

policy drop

I've tried commenting out the iptables and transparent_squid lines, with no effect on samba.

Any ideas?

---

### Post by AlistairHastings on 2009-01-03
Found a partial solution - removed all the "server xxx accept" lines and replaced with a single "server all accept".  Not ideal, but should do for now.

---


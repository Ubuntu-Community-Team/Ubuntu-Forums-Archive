---
title: "Configuring DNS resolver to query for AAAA before A"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by cmw on 2010-06-03
Hello,

I am running Ubuntu 10.04
I am also running miredo and have successfully obtained an IPv6 address on my Teredo interface.

ping6 ipv6.google.com successfully resolves to IPv6 address.  Wireshark packet captures verify connectivity on teredo interface.
ping6 [www.kame.net]("http://www.kame.net") also resolves to ipv6 address.
nslookup only returns A records unless I use 'set type=aaaa'

Using Firefox to go to [www.kame.net]("http://www.kame.net") or [www.gogo6.com]("http://www.gogo6.com") only leads to IPv4 version of each site.
Using Firefox to go to [http://](http://)[2001:200:0:8002:203:47ff:fea5:3085]/ causes the KAME turtle to dance.  
Connectivity isn't an issue, DNS resolution is my problem.

I have tried adding both 'options inet6' and 'family inet6 inet4' to /etc/resolv.conf but neither has forced DNS resolver to query for AAAA before A.

If anyone has a suggestion on how to configure Ubuntu to query for AAAA before A I will appreciate it.

Thx.

---


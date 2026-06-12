---
title: "Transparent Proxy Couldn't Work from WAN Network"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by Abu Hauna on 2009-09-02
Dear Ubuntuers...

I have two network segments with different locations.
Example :
- location A : segment network : 172.17.0.0/16 
(with internet gateway for local : 172.17.0.7)

- location B : segment network : 172.18.0.0/24

Network A & B already connected by International Infrastructure Qonnection.

Firewall & Proxy in segment Location A are managed by iptables & squid. It's work and running in segment network A client computers. And use transparent proxy as well. Default 3 chains iptables (INPUT, OUTPUT, FORWARD) are droped.

But, In Location B segment network, transparent proxy from 172.17.0.7 couldn't work.
Are there additional configuration about my iptables or squid in Location A ??

Please help me... !!!
Thanks

---

### Post by Abu Hauna on 2009-09-03
sorry, just renew...

---


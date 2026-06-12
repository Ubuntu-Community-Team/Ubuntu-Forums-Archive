---
title: "Iptable -&gt; ufw conversion"
date: 2013-02-13
forum: Networking &amp; Wireless
---

### Post by jojol on 2013-02-13
Hi,
 
I am stuck on something :
 
How could I effectively convert these lines :
 
```

iptables -A FORWARD -i eth0 -o tun0 -m state --state ESTABLISHED,RELATED -j ACCEPT 
iptables -A FORWARD -s 10.9.8.0/24 -o eth0 -j ACCEPT 
iptables -t nat -A POSTROUTING -s 10.9.8.0/24 -o eth0 -j MASQUERADE

```In ufw before.rules ?
 
 
Tried :
```

*nat
:POSTROUTING ACCEPT [0:0]
#Forward [custom]
-A FORWARD -i eth0 -o tun0 -m state --state ESTABLISHED,RELATED -j ACCEPT
-A FORWARD -s 10.9.8.0/24 -o eth0 -j ACCEPT
-t nat -A POSTROUTING -s 10.9.8.0/24 -o eth0 -j MASQUERADE

```and 
```
*nat
:POSTROUTING ACCEPT [0:0]
#Forward [custom]
-A ufw-before-forward -i eth0 -o tun0 -m state --state ESTABLISHED,RELATED -j ACCEPT
-A ufw-before-forward -s 10.9.8.0/24 -o eth0 -j ACCEPT
-t nat -A POSTROUTING -s 10.9.8.0/24 -o eth0 -j MASQUERADE

```any idea ?
 
Thanks,
 
Jojol

---


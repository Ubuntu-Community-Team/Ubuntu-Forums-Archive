---
title: "How To Setup Simple Port Forwarding"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by curtlee2002 on 2009-03-12
I am on a mixed network of computers.  Some have direct Internet ip's and some don't.  On one of the computers that has a direct Internet ip, I would like to forward connects to its port 80 to another computer on the network that doesn't have a direct Internet ip.  I read a lot of iptables' documentation and came up with what I did below, but it doesn't seem to work.

Thank you for your time,
-Curt Lee


```
# iptables -A FORWARD -p tcp -i eth0 -o eth0 -d 10.192.17.200 --dport 80 --sport 80 -m state --state NEW -j ACCEPT
```

```
# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             10.192.17.200       tcp spt:www dpt:www state NEW 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```

---


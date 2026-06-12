---
title: "iptables configuration"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by NilPointer on 2011-10-15
I've decided to reconfigure my firewall, since there was too many garbage rules and firewall seemed to block all connections. I've cleared all tables and added rules for ports, that i want to be open. Here's output of iptables -L

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain INBOUND (0 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:4445 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4445 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:4444 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4444 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:25600 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:25600 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:50000 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:50000
```

So, I want to block all ports, excluding 4444, 4445, 25600 and 50000. Will these rules do that job? Thanks in advance.

---


---
title: "Xbox Live Nat error"
date: 2012-04-24
forum: Networking &amp; Wireless
---

### Post by cmacia06 on 2012-04-24
I have seen this asked many times before but no responses. I connect my xbox 360 to the laptops Ethernet port. share to other computers is on and all goes well but when i test connection the ubuntu system is blocking port 3074 and possibly 88. Im guessing that the problem is the iptables not configured to forward all ports. Can somebody tell how to set that up so that port 3074 tcp and udp get forwarded. 

This is my iptables when xbox is connected to ethernet
```

sudo iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere             udp dpt:bootps
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:bootps
ACCEPT     udp  --  anywhere             anywhere             udp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:domain

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             10.42.0.0/24         state RELATED,ESTABLISHED
ACCEPT     all  --  10.42.0.0/24         anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

```

---


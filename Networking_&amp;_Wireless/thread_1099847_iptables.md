---
title: "iptables"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by sinclair86 on 2009-03-18
Ok tried searching google but I dont think Im wording it right. I'm not even sure if I should be posting this here or in programming. What Im trying to do is check the dest of a packet and if it matches, lets say  dest of 172.16.1.100, this is what I have now

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             172.16.1.100        

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy DROP)
target     prot opt source               destination 
```

new incoming ip is something like 123.123.123.123

I want to be able to add the following rules 
-A OUTPUT -d 123.123.123.123 -j ACCEPT
-A INPUT -s 123.123.123.123 -j ACCEPT

I know that second rule is redundant but I dont know another way to check the source of a packet and if its good then add 2 rules iptables

---


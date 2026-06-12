---
title: "help iptables"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by randumnumber on 2010-01-23
Hello I am trying to pass all incoming traffic from my internal network out to an external IP address. something like this 

internal network --> server --> external ip

i have it set up where i can pass the internal network out of the server into the internet to whatever page they are requesting, but what i want is for all page requests to goto a specific page on the internet, say google.com i have been trying to use this 

```
iptables -t nat -A PREROUTING -p tcp -j DNAT --to 'ip address of external page' 
```but it doesn't work

right now i have my ip tables set up like this 

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     

```and my nat tables like this

```
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
DNAT       udp  --  anywhere             anywhere            udp dpt:domain to:192.168.1.1 
DROP       all  --  192.168.1.128/25     192.168.1.0/25      
DNAT       udp  --  anywhere             anywhere            udp dpt:domain to:192.168.1.1 

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  anywhere             anywhere            
MASQUERADE  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


```as you can see i have dns setup so that internal computers can request sites and then they can pass though the server onto the internet.

there are a few repeats in my ip tables ignore them for now...i entered them twice


any help or pointers?

---


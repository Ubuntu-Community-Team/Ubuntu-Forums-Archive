---
title: "Vuze / Azureus UDP only as root"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by moffa on 2011-04-03
Whenever I run the UDP firewall test, I get:

Testing port UDP 500 ... 
    Sending outbound packet and waiting for reply probe (timeout=5000)
    Sending outbound packet and waiting for reply probe (timeout=10000)
    Sending outbound packet and waiting for reply probe (timeout=15000)
    Sending completion event
NAT Error. Inbound test failed, Transport unavailable, Permission denied.

But if I run Vuze as root, it's successful.  Any idea what permissions to change to allow it to accept UDP connections?

I'm using sun-java, already setup iptables, and forwarded the ports from my router correctly.

```
Iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:isakmp state NEW 

```

---


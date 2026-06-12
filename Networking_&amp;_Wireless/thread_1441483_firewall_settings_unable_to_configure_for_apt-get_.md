---
title: "firewall settings: unable to configure for apt-get and dns"
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by leesiulung on 2010-03-28
I have tried various rules, like opening port 53 for the DNS with little success. I finally figured that you need to set the source port to 53 and NOT the destination port.
 
However, I have been unable to figure out what ports apt-get requires. The only way I get it to work is to accept everything in iptables.
 
Anyone can give me some pointers?

---

### Post by leesiulung on 2010-03-28
I figured it out. DNS uses both tcp and udp on port 53 and apt-get uses tcp 80.
 
The rules are as follows:
 
```

# DNS
-A INPUT -p tcp -m tcp --sport 53 -j ACCEPT
-A INPUT -p udp -m udp --sport 53 -j ACCEPT

# apt-get
-A INPUT -p tcp --sport 80 -j ACCEPT

```
 
I hope this helps someone else in the future!

---


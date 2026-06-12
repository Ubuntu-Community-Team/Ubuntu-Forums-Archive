---
title: "iptables: multiple -m switches in 1 rule"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by lowrider2025 on 2011-01-20
How is it possible to write something like this ?

```
iptables -A INPUT -p tcp -s $ME -m mac --mac-source $MAC_ME -d $WEBSERVER --dport 2222 -m state --state NEW,ESTABLISHED -j ACCEPT -m comment --comment "incoming SSH request by Me"
```

does it have to be split in several rules ?
what I want is:
check for source ip and mac, destination port,state and add a comment

---

### Post by lowrider2025 on 2011-01-21
I thought I made a syntax error using multiple matches in 1 rule but I found the mistake. I forgot to change 1 variable whilest copy pasting. Issue is solved.

---


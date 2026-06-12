---
title: "IPTABLES and restricting local traffic"
date: 2012-01-24
forum: Networking &amp; Wireless
---

### Post by wdtd on 2012-01-24
I have a friend's PC that I want to give ONLY Internet access while preventing it from accessing anything on the local network. Unfortunately, at the moment, physically separating it is not possible although that would be my preferred solution.

I keep only finding tutorials for "preventing Internet access while allowing local access" and preventing access to the local network. Can I use iptables on the router PC to make that work?  Would I want FORWARD or INPUT? Would either of these work?

```
iptables -A FORWARD -s 192.168.1.3 -d 192.168.1.2 -j DROP
``````
iptables -A INPUT -m mac --mac-source 00:00:00:00:00:00 -d 192.168.1.0/255.255.255.0 -j DROP
```

---

### Post by scarecrow77 on 2012-06-14
Hey!

I'm looking for the exact same thing! (blocking ips on the LAN talking to each other rather than to the internet) did you have any luck solving your problem? I've been looking for an answer for days now...

Thanks! :)

---


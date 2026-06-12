---
title: "New User: How to block ports"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by pepsicokeman94 on 2010-03-12
I'm new to linux, just wondering how I can block upload from bitTorrent Transmission Client?

---

### Post by nixscripter on 2010-03-12
You can write a rule to block ports 6881 to 6889 in a firewall (such as [Firestarter]("https://help.ubuntu.com/community/Firestarter")).

This should do it in [iptables]("https://help.ubuntu.com/community/IptablesHowTo"), which is more the hacker approach:

```
iptables -A INPUT -d localhost -m multiport --dports 6881-6889 -j DROP
```

---


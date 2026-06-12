---
title: "Can't connect to wireless network after update"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by rstoya05-lx on 2009-04-12
I did an update yesterday and have had trouble connecting to a secured wireless network (WEP), which was working before. 

The following appears over and over in my /var/log/syslog:

```
eth1: authenticate with AP 00:06:25:5d:3b:ab
eth1: deauthenticated
eth1: authenticate with AP 00:06:25:5d:3b:ab
eth1: deauthenticated

```

I've rebooted multiple times and on occasion it connected but it's inconsistent. What I noticed is that in those cases the AP listed in the log is not the one above 00:06:25:5d:3b:ab.

---


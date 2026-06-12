---
title: "Squid restart with -D option"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by Barriehie on 2009-06-22
So I've tried:
```

sudo /etc/init.d/squid -D restart

```
and
```

sudo /etc/init.d/squid restart -D

```
and in both cases squid goes through the DNS testing of my external blacklist.  How to avoid this and at that point does squid do the DNS lookup on a per request basis???

Thanks in advance,
Barrie

---


---
title: "Confusing Bind Error"
date: 2013-02-22
forum: Networking &amp; Wireless
---

### Post by kramer2718 on 2013-02-22
Hi guys!

So I am attempting to start a service and getting a bind error.  The thing is, netstat does not show the port as being bound.

So I would like to know what logs to tail in order to see what is going on here.

Thanks in advance!

---

### Post by Doug S on 2013-02-22
I'm not sure I understand, but suggest this:```
grep named /var/log/syslog | more
```

---


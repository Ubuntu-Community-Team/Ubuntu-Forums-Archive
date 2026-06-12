---
title: "IP Route Add."
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by sunpyo on 2009-09-09
I got a pretty noobish question here. I'm very new to ubuntu and need to add an IP Route so that my computer can reach the internet. Normally in DOS I would write something to the affect of:
 
Route add 0.0.0.0 mask 0.0.0.0 192.168.1.253
 
However I have no idea how I would translate that in the ubuntu terminal. Any help would be appreciated.

---

### Post by uncle-c on 2009-09-09
Something like this :

```
$ route add default gw ***.***.***.*** eth0
```

---


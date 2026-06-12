---
title: "pppoeconf doesn't detect my modem"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by leoh on 2010-03-07
Hi everyone.
I just installed Ubuntu 9.10.
I ran sudo pppoeconf and it detected eth0 and wlan0.
However, it doesn't detect my DSL modem.
The modem works fine, if I connect the same modem to another Win computer it works.
How can I fix this?

---

### Post by dineshs on 2010-03-08
On a terminal type
```
ifconfig -a
```
and post the output

---


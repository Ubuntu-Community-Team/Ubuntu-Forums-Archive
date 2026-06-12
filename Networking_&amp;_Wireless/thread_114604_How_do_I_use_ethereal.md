---
title: "How do I use ethereal"
date: 2006-01-08
forum: Networking &amp; Wireless
---

### Post by zappa86 on 2006-01-08
Whenever I try to open ethereal it crapps out. Also when I try tethereal from the shell it gives me this error:
```
root@zappa:/home/harry# tethereal
Could not set capabilities: Operation not permitted

```
anyone know what that error means.
Ive tried it with -v too and I get no extra info. Does anyone know how to use this or a good packet sniffing program. I need to figure out why this other net program is not working. I need something more sophicated than tcpdump

---

### Post by towsonu2003 on 2006-01-08
try ```
ethereal
``` or as a regular user ```
sudo ethereal
```

---

### Post by zappa86 on 2006-01-08
thanks that how to get to regular ethereal. a little googleing and I figured it out. I needed to load a module actually called capability so I just did a 
```
modprobe capability
```
and I was good to go. I wish the error output made it easer to know that is what must be done.

---


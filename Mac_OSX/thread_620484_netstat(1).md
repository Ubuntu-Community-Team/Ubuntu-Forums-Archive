---
title: "netstat(1)"
date: 2007-11-22
forum: Mac OSX
---

### Post by arijarot on 2007-11-22
On netstat(8 ), to show the PID and program name I use ```
netstat -p
```. I looked at the man for netstat(1) (on os x 10.4) but can't find the equivalent or similar command. Does anyone know what if there is such a thing?

---

### Post by stmiller on 2007-11-23
Yeah weird BSD. Try this in OS X to get something similar:

```
sudo lsof -i -P
```

---

### Post by arijarot on 2007-11-23
> **stmiller said:**
> Yeah weird BSD. Try this in OS X to get something similar:

```
sudo lsof -i -P
```

Seems promising. Thanks a lot.

---


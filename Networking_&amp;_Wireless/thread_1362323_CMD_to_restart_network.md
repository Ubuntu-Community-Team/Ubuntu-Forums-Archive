---
title: "CMD to restart network"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by sggin on 2009-12-23
hi,

How do u force a network card to restart ubuntu studio 9.1?

thanks

---

### Post by kerry_s on 2009-12-23
```
sudo /etc/init.d/networking restart
```

---

### Post by sggin on 2009-12-23
ty for the help

---

### Post by prshah on 2009-12-23
> **sggin said:**
> 
How do u force a network card to restart ubuntu studio 9.1?

From 9.10 onwards, please use the "service" command```
sudo service networking restart
``` though the older ```
sudo /etc/init.d/networking restart
``` command will work as well, but may not for future platforms.

---


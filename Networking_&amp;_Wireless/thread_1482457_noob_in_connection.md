---
title: "noob in connection"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by paradoxboi on 2010-05-13
hello.....
i have a big problem regarding to connect to internet using broadband...some how i cant connect to it...someone pls help me to figure out this thing...

---

### Post by Iowan on 2010-05-13
Might need just a bit more information...
Cable or DSL (or 3G?)?
From a terminal (Applications>Accessories>Terminal) check:```
ifconfig -a
```If no IP address is associated with the interface, check (post if possible) ```
sudo lshw -C network
```

---

### Post by paradoxboi on 2010-05-13
3g..i use siera wireless modem

---


---
title: "Cant edit auto eth0"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by mshenrick on 2010-05-02
in my networking settings on lucid (fresh install), i cannot edit/delete auto eth0

---

### Post by Iowan on 2010-05-04
Did you get Lucid un-installed, or is Auto eth0 still in need of edit? From a terminal (Applications>Accessories>Terminal) check **ifconfig -a** to see if the interface is recognized at all. **sudo lshw -C network** will be the next step...

---


---
title: "hp 530 wifi drivers"
date: 2013-08-02
forum: Networking &amp; Wireless
---

### Post by filippo2 on 2013-08-02
Hi all! I write my first post for the following problem: after i installed lubuntu 13.04 on an hp 530, the wireless does not works. I think i don't have drivers and don't know how to install them when i'll get them with your help.

Thanks a lot,

---

### Post by chili555 on 2013-08-02
Let's identify your wireless device so we can decide what driver you need. Please open a terminal and run and then post:```
lscpi -nn | grep 0280
```Thanks.

---

### Post by filippo2 on 2013-08-02
termilal says "commandnot found"...

---

### Post by chili555 on 2013-08-02
Are you sure you typed it correctly?```
lscpi -nn | grep 0280
```That's lower case for LSPCI.

---


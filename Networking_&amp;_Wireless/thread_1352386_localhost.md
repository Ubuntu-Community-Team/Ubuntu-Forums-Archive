---
title: "localhost"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by david90 on 2009-12-11
What is the significant of the machine name localhost?  What is it use for and when do I need to change it?

---

### Post by adaucourt on 2009-12-11
> **david90 said:**
> What is the significant of the machine name localhost?  What is it use for and when do I need to change it?

localhost is a standard for referring to your local machine sometime commonly replaced with 127.0.0.1 (loopback), it doesnt change even if your computer name changes.

for instance you can:
ping localhost

you can:
ping 127.0.0.1

you can:
ping yourcomputername

and they would all yield the same result... just a generic way of calling your machine.

---

### Post by Iowan on 2009-12-11
Changing it isn't advised. There's another line in the */etc/hosts* file that also describes your machine. 127.0.1.1 usually has your machine hostname (the one you chose when setting it up).

---


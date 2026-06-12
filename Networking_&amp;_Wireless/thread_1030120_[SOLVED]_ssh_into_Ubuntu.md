---
title: "[SOLVED] ssh into Ubuntu"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by cjv8888 on 2009-01-04
I am able to ssh into my Ubuntu Hardy desktop from my eeepc running Xandros, but all I got is a terminal of the Hardy computer.

How do I open up nautilus or a file manager GUI to make it easier to work with?
Thanks in advance.

---

### Post by Peter09 on 2009-01-04
try
```
ssh -X <user>@<machine> nautilus
```

---

### Post by cjv8888 on 2009-01-04
> **Peter09 said:**
> try
```
ssh -X <user>@<machine> nautilus
```

Thanks, problem solved in 3 minutes.
X has to capital or small letter?

---

### Post by Peter09 on 2009-01-04
Capital X

---


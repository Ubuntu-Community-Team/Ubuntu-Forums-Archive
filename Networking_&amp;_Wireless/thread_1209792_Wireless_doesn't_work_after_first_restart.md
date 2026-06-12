---
title: "Wireless doesn't work after first restart"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by just4now on 2009-07-10
After installing ubuntu, my wireless works and after I restart my computer wireless doesn't show up on the wireless manager

---

### Post by earthpigg on 2009-07-10
can you show us the output of this command, please:

sudo iwlist scanning

---

### Post by Crafty Kisses on 2009-07-10
> **just4now said:**
> After installing ubuntu, my wireless works and after I restart my computer wireless doesn't show up on the wireless manager

Sounds like the module for this card is not loading at boot. What are the results for the following commands?
```
lspci
lsmod
```

---

### Post by just4now on 2009-07-24
Sorry guys, now it magically works and a couple re installations.

I guess its one of ubuntu's quirks?

---


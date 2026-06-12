---
title: "nfs exports with spaces"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by yee379 on 2009-04-25
i'm trying to serve a directory with a space in the pathname. i'm using 8.1 and nfs-kernel-server.

i've tried single quotes (it ignores the path after the space, and says it doesn't exist)
i've tried double quotes (says 'does not support NFS export')
i've tried with \040 as space (says 'does not support NFS export')

any suggestions? thanks!

---

### Post by whoop on 2009-04-25
Does a "\ " work for each space (omit the double quotes)?

---

### Post by yee379 on 2009-04-25
> **whoop said:**
> Does a "\ " work for each space (omit the double quotes)?

nope - it seems to exclude the characters after the escaped space :(

---

### Post by dannyboy79 on 2011-12-06
an oldie but goodie, anyone know anything about sharing our directories which have spaces? I've tried googling, I've tried using quotes, i've tried \ , I have tried using %20 and %40, nothing is working. THoughts?

---


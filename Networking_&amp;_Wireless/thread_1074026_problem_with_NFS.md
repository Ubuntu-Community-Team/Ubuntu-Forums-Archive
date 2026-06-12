---
title: "problem with NFS"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by articwolf939 on 2009-02-18
im following the how to and im to the point where i need to add things to me /etc/exports file and i have the termal open to the right place and i type

/files 192.168.1.0/24(rw,no_root_squash,async)

in and i get E486: pattern not found: files 192.168.1.0

Im kinda lost o.O

---

### Post by handy on 2009-02-19
See if we can get this moved to Network & Wireless sub-forum, you will do better there.

---

### Post by dmizer on 2009-02-19
Moved to Networking and wireless.

How are you trying to edit /etc/exports?

Try this:
```
gksudo gedit /etc/exports
```

---


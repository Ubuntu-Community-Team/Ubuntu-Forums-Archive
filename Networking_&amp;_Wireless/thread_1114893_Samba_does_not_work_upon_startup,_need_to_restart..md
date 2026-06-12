---
title: "Samba does not work upon startup, need to restart."
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by CptanPanic on 2009-04-03
I am running 8.04.2.  When I boot up the nmbd fails to start because it seems that the machine hasn't gotten its ip address yet via dhcp.  How can I fix this?
```

create_subnets: unable to create any subnet from given interfaces. nmbd is terminating
```

---

### Post by CptanPanic on 2009-04-04
Anyone?

---

### Post by CptanPanic on 2009-04-08
I tried putting a sleep 30 in the samba startup script but that didn't help.  How can I change the order that it starts up with?

---

### Post by Iowan on 2009-04-09
Dunno if it's practical, but you can jockey the number in /etc/rcX.d.  My (Breezy) server has** S20samba** in* /etc/rc2.d*.

---


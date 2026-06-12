---
title: "dsl problem"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by alenn on 2010-06-09
I made dsl connection but I can't establish that connesction because there is no connection icon. Before I installed Ubuntu 10.04 that icon was next to shut down button but now it's gone, can you help me.

---

### Post by alenn on 2010-06-09
plz help me

---

### Post by ronnielsen1 on 2010-06-09
I'm using 9.10 but it should be the same way. Right click on taskbar, add to panel, network monitor

---

### Post by alenn on 2010-06-09
I already tried that but there is no network monitor on the list of programs which I can set.

---

### Post by alenn on 2010-06-09
I tried reinstalling network manager and it's the same again.

---

### Post by dineshs on 2010-06-09
Try this
1.Check nm-system-settings.conf
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```
and set
```
managed=true
```
2.While configuring DSL via NM tick the option _available to all users_

---

### Post by alenn on 2010-06-09
ok, tnx that helped me, but what to type in box named service??

---

### Post by dineshs on 2010-06-09
Anything -say your ISP name

---

### Post by alenn on 2010-06-09
ok, tnx, I fixed it, it's now working perfectly.

and sorry for bad english  :)

---


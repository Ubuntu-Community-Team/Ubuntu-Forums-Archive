---
title: "xfmedia segfault after update to jaunty"
date: 2009-04-30
forum: Multimedia Software
---

### Post by mohr tutchy on 2009-04-30
After an update from intrepid to jaunty xfmedia won't run.
```
$xfmedia
Segmentation fault
$dmesg|grep xfmedia
[ 2608.836874] xfmedia[15172]: segfault at 726f78 ip b75d69e0 sp bff448b4 error 4 in libpthread-2.9.so[b75cf000+15000]

```

The weird issue is that it run without any problem as root.
```
$sudo xfmedia
```

Deleting configuration files doesn't help.

Help me please! Thanks :)

One love

---

### Post by tbraun on 2009-05-07
Same issue here. If someone knows what to do, please let us know.

---

### Post by anv on 2009-07-31
started to work with sudo also here ( 32 bit xubuntu)

---


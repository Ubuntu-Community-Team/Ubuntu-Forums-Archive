---
title: "intel 82801cam ethernet not work in ubuntu"
date: 2011-08-20
forum: Networking &amp; Wireless
---

### Post by carlofabyss on 2011-08-20
hi I have an old sony vaio laptop, and it has an intel 82801cam ethernet device and it refuses to work when I plug it in to an ethernet adapter. Im thinking it is a driver issues but whenever I list my hardware devices in terminal with lshw it seems to see that device despite that. Any suggestions? Thanks in advance

---

### Post by praseodym on 2011-08-21
Hello,

can you post the following terminal outputs:

```
lspci -nnk | grep -iA2 net
uname -a
lsmod
ifconfig -a
cat /etc/udev/rules.d/70-persistent-net.rules
```

---


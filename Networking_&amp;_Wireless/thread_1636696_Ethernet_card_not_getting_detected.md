---
title: "Ethernet card not getting detected"
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by arunkumar2111 on 2010-12-03
I have brought a new DELL INSPIRON 1410. I installed ubuntu 10.04 but my ethernet card is not getting detected where as in windows 7 is working.... Please help

---

### Post by MooPi on 2010-12-03
Can you give us the results of these commands in terminal
```
lspci
```
```
ifconfig
```
```
lsmod
```

---

### Post by endotherm on 2010-12-03
and while you're at it:
```

ifconfig -a
cat /etc/network/interfaces

```

---


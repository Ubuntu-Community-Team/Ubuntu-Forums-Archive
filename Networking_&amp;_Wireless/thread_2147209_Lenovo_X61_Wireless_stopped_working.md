---
title: "Lenovo X61: Wireless stopped working"
date: 2013-05-21
forum: Networking &amp; Wireless
---

### Post by TheHimself on 2013-05-21
I have Xubuntu 12.4 on  Lenovo X61. The wireless suddenly stopped working. Its LED is off. Network manager can find networks but cannot connect to them. When I run iwconfig, it says ESSID: off/any, Mode:managed, Access point: not-associated, Power management off, RTS thr: off. How can I figure out if this is a software or hardware problem?

---

### Post by praseodym on 2013-05-21
Please show these outputs:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
in Code-Tags ('#'-Symbol)

---

### Post by TheHimself on 2013-05-21
I can't transfer any files from the computer to the internet unfortunately. I have a kind of connection disaster; my cellphone doesn't connect to wifi anymore, the wired internet at home broke and my laptop doesn't connect to the ethernet at work. ](*,)](*,)](*,)

---

### Post by praseodym on 2013-05-21
Screenshots?!

---


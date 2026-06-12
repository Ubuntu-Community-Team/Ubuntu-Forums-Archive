---
title: "dongle connection"
date: 2011-08-16
forum: Networking &amp; Wireless
---

### Post by madusha on 2011-08-16
i use a dongle made by Option in windows xp, i started to use Ubuntu some time later , i can't connect with my dongle. If i can do it, i'm gonna stop using windows. Please any1 help me

---

### Post by praseodym on 2011-08-21
Hello,

can you show the following terminal outputs:

```
lspci -nnk | grep -iA2 net
lsusb
pccardctl info
lsmod
rfkill list
```

---

### Post by raja.genupula on 2011-08-21
> **madusha said:**
> i use a dongle made by Option in windows xp, i started to use Ubuntu some time later , i can't connect with my dongle. If i can do it, i'm gonna stop using windows. Please any1 help me

go to network connections at your panel  , edit connections , click at mobile broadband , click at new and you will know how to go next all simple steps . give your apn , number *99# , username & password as empty .  click save . then look at your network connection at panel . you'll have it .

---


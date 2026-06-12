---
title: "ASUS X53E-SX1186V Wireless not working."
date: 2012-02-20
forum: Networking &amp; Wireless
---

### Post by _eKKo_ on 2012-02-20
Hey guys.

So I recently purchased the ASUS X53E-SX1186V and went to install ubuntu 10.10. Unfortunately the wireless nor the LAN drivers seem to work. I've done some searching around the net and I think (from what I gathered), that it has the Intel Centrino N-100 wireless in there.

I installed ubuntu 11.10 and the wireless works fine in there, however I'd prefer to use ubuntu 10.10.

Any help would be greatly appreciated.

EDIT i have this laptop:
[http://www.amazon.co.uk/ASUS-LAPTOP-I5-2430-2-3GHZ-750GB/dp/tech-data/B00785YHIQ/ref=de_a_smtd](http://www.amazon.co.uk/ASUS-LAPTOP-I5-2430-2-3GHZ-750GB/dp/tech-data/B00785YHIQ/ref=de_a_smtd)

-eKKo

---

### Post by praseodym on 2012-02-20
Please show:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by nikonian on 2012-09-16
You spent nine HUNDRED pounds on that? I have the X53E-SX996V which has i7-2670QM which appears to be a FAR superior CPU + 4Gb DDR3, ... for £500!

Wow, seriously, I think you got fleeced.

---


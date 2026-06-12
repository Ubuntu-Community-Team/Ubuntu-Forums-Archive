---
title: "Wireless activation"
date: 2013-06-04
forum: Networking &amp; Wireless
---

### Post by kellyhenry on 2013-06-04
Why can't I activate my Wireless on my hp mini110? This is really annoying. please help me with this issue. i'll be really grateful

---

### Post by praseodym on 2013-06-04
Please open a terminal with CTRL+ALT+T and show these outputs:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---


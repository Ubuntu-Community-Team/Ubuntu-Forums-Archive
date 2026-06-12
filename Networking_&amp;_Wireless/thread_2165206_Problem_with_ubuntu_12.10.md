---
title: "Problem with ubuntu 12.10"
date: 2013-08-03
forum: Networking &amp; Wireless
---

### Post by Javed_iqbal on 2013-08-03
i have bought DELL 3420 and having ubuntu 12.10 installed now but the wifi doesnt connects..is it drivers issue or something else...i need it badly....plz guide me in this regard

---

### Post by praseodym on 2013-08-04
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---


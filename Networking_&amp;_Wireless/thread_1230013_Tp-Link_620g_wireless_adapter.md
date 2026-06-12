---
title: "Tp-Link 620g wireless adapter"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by dmillerw on 2009-08-02
Has anyone had luck using the TP-Link 620G wifi adapter in Ubuntu 9.04?

I've tried, but am not quite sure how to install the drivers using ndiswrapper and getting Ubuntu to recognize them.

---

### Post by pytheas22 on 2009-08-02
Please open a terminal from the Applications>Accessories menu and post the output of these commands:
```

lsusb
lspci -nn
uname -rm
lshw -C Network
```

---


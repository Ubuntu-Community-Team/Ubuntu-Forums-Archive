---
title: "Wireless With Belkin Help"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by Apv507 on 2010-05-28
I bought this and found out it wasn't support on Ubuntu at all.. but is there anything I can do that does not involve virtualbox. its a Belkin f7d1101. Is it possible to make a driver?

---

### Post by flash63 on 2010-05-29
Hello,
build-in Chipset and Device-ID's?

For PCI-Cards:
```
lspci -nnk | grep -i net -A2
```
For USB-Devices
```
lsusb
```

---


---
title: "network driver"
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by nintoantony on 2010-12-08
how to install network card driver in ubuntu 9.01.
configuration:-
intel core i3
4gb ram
atheros ar8152 pci-e fast ethernet controller

---

### Post by chili555 on 2010-12-08
Please open Applications > Accessories > Terminal and do:```
lspci -nn | grep -i ethernet
sudo modprobe atl1c
dmesg | grep atl
```Post the result and we'll proceed.

---


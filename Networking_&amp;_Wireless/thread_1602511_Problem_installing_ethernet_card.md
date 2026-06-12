---
title: "Problem installing ethernet card"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by nHacker on 2010-10-21
I recently installed an Intex PCI Ethernet Card (model no. IT-584) on my PC. It works perfectly in Windows even without installing the given drivers. But it doesn't seem to work in Ubuntu. The network icon displays 'disconnected'. I tried to install the driver from the given CD, there I found a rtl8139.c file and tried to compile it, but couldn't. I also downloaded a compiled .o file ([http://www.szabilinux.hu/rtl8139/rtl8139.o](http://www.szabilinux.hu/rtl8139/rtl8139.o)) and tried to install it, but there were errors:
```

sudo insmod rtl8139.o
insmod: error inserting 'rtl8139.o': -1 Invalid module format

```

Now I don't know what to do. Please help.

---


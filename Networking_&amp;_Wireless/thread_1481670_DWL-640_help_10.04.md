---
title: "DWL-640 help 10.04"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by igsimon on 2010-05-12
I have the DWL-630 PCMCIA wireless adapter.
My problem is... the computer doesn't recognize it. It doesn't light up and the computer doesn't seem to know that it's there.

Can someone point me to instructions or explain exactly what I have to do to make the system recognize and use the DWL-630 PCMCIA wireless adapter?

---

### Post by igsimon on 2010-05-12
sorry it should be DWL-G630  how do i compile  / load driver from [http://www.dlinkla.com/home/productos/producto.jsp?idp=709](http://www.dlinkla.com/home/productos/producto.jsp?idp=709)

---

### Post by chili555 on 2010-05-12
Please open a terminal and do:```
sudo modprobe rt61pci
iwconfig
dmesg | grep 61
```Please post the results. Thanks.

---

### Post by CoopsMgoops on 2011-08-16
I am also having a similar problem but my computer will recognize the pc card it just doesnt know what to do with it. Maybe I could just download the driver or something but I cant find it for Ubuntu.

Thanks!


IBM A31p, Ubuntu Studio 11.04

---


---
title: "Ubuntu 10.10 and a WMP54G Wireless-G PCI adapter"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by infernowolf36 on 2010-11-24
hello i'm trying to get a WMP54G Wireless-G PCI working with ubuntu 10.10 .. my system recognizes the wifi card but it says it's 'missing firmware' any help would be appreciated.

---

### Post by grahammechanical on 2010-11-24
Here is the trouble shooting guide.

[https://help.ubuntu.com/community/WifiDocs/](https://help.ubuntu.com/community/WifiDocs/)

Look to see if your network card is supported by the kernel. You may need to use the Windows drivers through something called ndiswrapper.

Regards.

---

### Post by chili555 on 2010-11-24
> i'm trying to get a WMP54G Wireless-G PCI working with ubuntu 10.10Many of these are based on the Broacom chipset. The proprietary firmware is not installed by default. Please open Applications > Accessories > Terminal and run:```
dmesg | grep b43
```It may report missing firmware.

Can you get a wired ethernet connection? If so, please go to System > Administration > Additional Drivers and activate the Broadcom driver. It will grab the firmware for you and install it in the correct location.

---

### Post by infernowolf36 on 2010-11-25
chili555,
"System > Administration > Additional Drivers and activate the Broadcom driver."
totally worked. i can't believe i forgot about that. thanks much. 

grahammechanical
thank you for the compatability list. :)

---


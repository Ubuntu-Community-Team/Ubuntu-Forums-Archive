---
title: "ubuntu 11.04 and wimax bm325"
date: 2011-09-30
forum: Networking &amp; Wireless
---

### Post by osamemail on 2011-09-30
I'm insalled ubuntu 11.04 64bit today, this is the first time i used ubuntu,it's look nice and better than win,anyway the problem here that i can't run the internet via wimax bm325 modem why? is there any driver for that.please help me

---

### Post by praseodym on 2011-09-30
Hi,

please show the terminal outputs of:

```
uname -a
lsusb
lsmod
usb-devices
```
Does it show up as a drive on your desktop/in the file manager? Check: Right-click on the drive icon and "remove safely". If it works, check again with "lsusb" if the device ID changed. Did you try to install the packages **usb-modeswitch** and **usb-modeswitch-data**?

---

### Post by pdc on 2011-10-01
so this is a Huawei modem

[http://yotatester.ru/art/Obzor_WiMAX_modema_Huawei_BM325](http://yotatester.ru/art/Obzor_WiMAX_modema_Huawei_BM325)

the device gets one mention on usb_modeswitch

[www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=331&sid=6896b499b53e15b8a07614b23dfdbb55](www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=331&sid=6896b499b53e15b8a07614b23dfdbb55)

the latest usb_modeswitch data file only seems to have an entry for a related device

> # Huawei BM358 WiMAX
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="380b", RUN+="usb_modeswitch '%b/%k'"


seems like the ID for this device might be 12d1:3808

we await more information from the owner

---


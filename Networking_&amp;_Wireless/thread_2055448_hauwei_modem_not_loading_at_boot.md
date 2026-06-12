---
title: "hauwei modem not loading at boot"
date: 2012-09-09
forum: Networking &amp; Wireless
---

### Post by spiky001 on 2012-09-09
Hi  I,m having a problem with hauwei 3g not loading at boot in 12.04 it did in 10.04. It has been set up in network manager, If I unplug the modem then replug it is recognised in NM. It also connects then to internet.   lsusb ```
Bus 001 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270/E870 HSDPA/HSUPA Modem
```  output of ls -al /dev/serial/by-id ```
lrwxrwxrwx 1 root root 13 Sep  9 15:20 usb-HUAWEI_Technology_HUAWEI_Mobile-if00-port0 -> ../../ttyUSB0 lrwxrwxrwx 1 root root 13 Sep  9 15:20 usb-HUAWEI_Technology_HUAWEI_Mobile-if01-port0 -> ../../ttyUSB1
```  I hope some one can assist it fixing this

---

### Post by spiky001 on 2012-09-10
Hi   I seemed to have fixed the problem as the dongle seemed to load on loading today. I found a fix from Alexfish by changing a line in /lib/udev/rules.d/40-usb_modeswitch.rules. But I have another problem that it wont connect to internet automatically I have to open network manager, It has enable mobile broadband as soon as I select it connects. I have checked and it is tick to start automatically in settings also any user is ticked. Any ideas to fix this problem.

---


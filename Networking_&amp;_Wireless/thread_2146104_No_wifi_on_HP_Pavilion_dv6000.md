---
title: "No wifi on HP Pavilion dv6000"
date: 2013-05-17
forum: Networking &amp; Wireless
---

### Post by citylife4 on 2013-05-17
Hii to all!!

I have a laptop HP pavilion  dv6000 with 13.04 and after installing this version of ubuntu i used to have wi-fi, but I had to use this command on the terminal 
```
 sudo modprobe b43 
```
but now, when I use that command the terminal enters in a infinit loop and doesnt get out...

anyone know how to fix this??

thanks!!

btw:
```

lsusb

Bus 001 Device 007: ID 12d1:1039 Huawei Technologies Co., Ltd. Ideos (tethering mode)
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 003 Device 002: ID 192f:0616 Avago Technologies, Pte. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

---

### Post by praseodym on 2013-05-17
Please show
```

lspci -nnk | grep -iA2 net
```
Did you install the package "linux-firmware-nonfree"?

---


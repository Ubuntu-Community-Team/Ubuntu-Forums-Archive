---
title: "eyeTV Hybrid is not working properly (does not create /dev/dvb)"
date: 2013-09-15
forum: Multimedia Software
---

### Post by stan4 on 2013-09-15
I've searched the internet and Ubuntu forums in particular, but couldn't find any information specific to my model, so I'm not sure if it's not supported or am I not doing something right.

Here are the dmesg and lsusb outputs:
```

[    2.814122] usb 1-1: New USB device found, idVendor=0fd9, idProduct=0031
[    2.814352] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.814547] usb 1-1: Product: EyeTV Hybrid
[    2.814680] usb 1-1: Manufacturer: Elgato Systems
[    2.814824] usb 1-1: SerialNumber: 100504009868




root@NAS:~# lsusb
Bus 001 Device 002: ID 0fd9:0031 Elgato Systems GmbH
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



```

I'm trying to get it to work with Tvheadend but it doesn't even display eyeTV in its settings, I'm thinking maybe because I don't have /dev/dvb created when eyeTV is plugged.

Is it just not supported or do I need to load drivers/firmware specific to this model (I've downloaded the Mac app which has firmware for eyeTV models, but I don't know which directory has the firmware corresponding to my model)?

thanks!

---


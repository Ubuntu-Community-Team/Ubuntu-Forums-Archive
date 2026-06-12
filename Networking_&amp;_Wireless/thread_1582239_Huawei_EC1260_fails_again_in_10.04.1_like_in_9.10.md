---
title: "Huawei EC1260 fails again in 10.04.1 like in 9.10"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by jre6 on 2010-09-26
I just recently switched from Ubuntu 9.04 to Ubuntu 10.04.1. Like Ubuntu 9.10, Networkmanager will not recognise the Huawei EC1260 until I do all this in a terminal:
```

sudo rmmod usb-storage
sudo modprobe usbserial vendor=0x12d1 product=0x140b

```
However, if I have plugged in a pen drive earlier, then the above methods fail, too.
This is a continuation of the problem that first appeared in 9.10  which has not been fixed yet (and [reportedly fixed]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146/+index?comments=all") in 10.04).
Are any workarounds available for this problem?

---

### Post by alexfish on 2010-09-26
hi

there have been a few reports of drivers not loading ,depending on kernel version

have you upgraded to the latest kernel,

is the system 64 bit or 32 bit

also of note you are loading the standard usbserial , so this may affect the performance of the device, so need to know if the device is 3g or cdma , from this it may be possible to determine which drivers to load.

---

### Post by jre6 on 2010-09-26
I am using 32 bit Ubuntu and the kernel is 2.6.32-24-generic. The maverick kernel doesn't fix this.
The device is CDMA.

---

### Post by alexfish on 2010-09-27
The device id's looks recent
 

 do you have latest usb_modeswitch installed
 

 [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)
 

 can't find id's in database so suggest
 

 Josua Dietze of usb_modeswitch forum may be able to help
 

 [ModeSwitchForum]("http://www.draisberghof.de/usb_modeswitch/bb/")
 

 regards
 

 alexfish

---


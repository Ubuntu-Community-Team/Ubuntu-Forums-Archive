---
title: "3G usb internet not recognised"
date: 2013-07-16
forum: Networking &amp; Wireless
---

### Post by stuwoody007 on 2013-07-16
I am trying to use a Metafone 3G usb internet but ubuntu will not recognize that it is plugged in. i have tried running the install off a separate usb but it still wont recognize that it is plugged in. yes the usb drives work i have checked this it is only with the 3g internet. Can anyone please help.

Please help, Stu

---

### Post by theDaveTheRave on 2013-07-16
hi,

plug the usb key in and from a terminal enter the following

```
ls usb
```

post the output of the code, specifically can you need to identify your new usb dongle in the output.

David

---

### Post by stuwoody007 on 2013-07-16
> **theDaveTheRave said:**
> hi,

plug the usb key in and from a terminal enter the following

```
ls usb
```

post the output of the code, specifically can you need to identify your new usb dongle in the output.

David

ls: cannot access usb: No such file or directory

It cant see it at all.

Thoughts dave?

---

### Post by stuwoody007 on 2013-07-16
> **stuwoody007 said:**
> ls: cannot access usb: No such file or directory

It cant see it at all.

Thoughts dave?

dell@dell-Vostro-2521:~$ lsusb 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
Bus 003 Device 007: ID 12d1:14b5 Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
Bus 001 Device 003: ID 0a5c:21d7 Broadcom Corp. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0c45:64ad Microdia 



second try

---

### Post by praseodym on 2013-07-16
Hi,

12d1:14b5 obviously is the "storage-mode" of the stick. Install "usb-modeswitch" via software-center to flip-flop to modem-mode.

---

### Post by stuwoody007 on 2013-07-16
usb-modeswitch is installed -how do i now use it? sorry but are a linux novice.  Cheers Stu

---

### Post by praseodym on 2013-07-16
Try this one via copy/paste:

```
sudo usb_modeswitch -v 12d1 -p 14b5 -M '55534243123456780000000000000011062000000100000000000000000000' 
```

---

### Post by stuwoody007 on 2013-07-16
Rodger that, this is what happened

Still cant find the device listed in network manager

Looking for default devices ... 
   found matching product ID 
   adding device 
 Found device in default mode, class or configuration (1) 
Accessing device 010 on bus 003 ... 
Getting the current device configuration ... 
 OK, got current device configuration (1) 
Using first interface: 0x00 
Using endpoints 0x01 (out) and 0x81 (in) 
Inquiring device details; driver will be detached ... 
Looking for active driver ... 
 No driver found. Either detached before or never attached

---

### Post by praseodym on 2013-07-16
Please check now
```

usb-devices
lsmod
lsusb
```

---

### Post by diazepamkit on 2013-07-16
u can use this way

[http://askubuntu.com/questions/143989/3g-usb-modem-not-working-in-12-04](http://askubuntu.com/questions/143989/3g-usb-modem-not-working-in-12-04)

---

### Post by stuwoody007 on 2013-07-16
Got it working - thanks for everyones help

---


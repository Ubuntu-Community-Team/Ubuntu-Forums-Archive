---
title: "Microdia PC Camera (SN9C120) with ubuntu 8.10"
date: 2009-03-08
forum: Multimedia Software
---

### Post by almsamim on 2009-03-08
my lsusb output :
```
Bus 005 Device 009: ID 0c45:613c Microdia PC Camera (SN9C120)
Bus 005 Device 008: ID 058f:6366 Alcor Micro Corp. 
Bus 005 Device 006: ID 058f:6254 Alcor Micro Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

i searched the forum and found that this webcam is supported but when trying to compile the source 

> sn9c1xx-1.48.tar.gz Popular  	Version: 1.48
Submitted Date:  2007/9/1
Description:
Video4Linux2 driver for SN9C101, SN9C102, SN9C103, SN9C105, SN9C120 PC Camera Controllers.
[http://www.linux-projects.org/modules/mydownloads/visit.php?cid=2&lid=44](http://www.linux-projects.org/modules/mydownloads/visit.php?cid=2&lid=44)

i get this error after "make"
```
**************************************************************************
* Building Video4Linux2 driver v1.48 for SN9C1xx PC Camera Controllers...*
* Official Linux 2.6.19 is the minimum version for this driver.          *
* Read the documentation "sn9c102.txt" for more informations.            *
* Type "make help" for a list of available targets.                      *
**************************************************************************

make -C /lib/modules/`uname -r`/build M=/home/abdullah/Desktop/sn9c1xx-1.48 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.o
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1033: warning: ‘struct class_device’ declared inside parameter list
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1033: warning: its scope is only this definition or declaration, which is probably not what you want
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_show_reg’:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1041: error: ‘struct video_device’ has no member named ‘class_dev’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1041: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1041: warning: initialization from incompatible pointer type
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1041: error: ‘struct video_device’ has no member named ‘class_dev’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: At top level:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1057: warning: ‘struct class_device’ declared inside parameter list
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_store_reg’:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1066: error: ‘struct video_device’ has no member named ‘class_dev’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1066: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1066: warning: initialization from incompatible pointer type
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1066: error: ‘struct video_device’ has no member named ‘class_dev’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: At top level:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1090: warning: ‘struct class_device’ declared inside parameter list
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_show_val’:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1099: error: ‘struct video_device’ has no member named ‘class_dev’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1099: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1099: warning: initialization from incompatible pointer type
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1099: error: ‘struct video_device’ has no member named ‘class_dev’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: At top level:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1122: warning: ‘struct class_device’ declared inside parameter list
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_store_val’:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1132: error: ‘struct video_device’ has no member named ‘class_dev’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1132: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1132: warning: initialization from incompatible pointer type
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1132: error: ‘struct video_device’ has no member named ‘class_dev’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: At top level:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1161: warning: ‘struct class_device’ declared inside parameter list
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_show_i2c_reg’:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1169: error: ‘struct video_device’ has no member named ‘class_dev’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1169: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1169: warning: initialization from incompatible pointer type
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1169: error: ‘struct video_device’ has no member named ‘class_dev’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: At top level:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1187: warning: ‘struct class_device’ declared inside parameter list
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_store_i2c_reg’:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1196: error: ‘struct video_device’ has no member named ‘class_dev’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1196: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1196: warning: initialization from incompatible pointer type
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1196: error: ‘struct video_device’ has no member named ‘class_dev’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: At top level:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1220: warning: ‘struct class_device’ declared inside parameter list
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_show_i2c_val’:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1229: error: ‘struct video_device’ has no member named ‘class_dev’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1229: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1229: warning: initialization from incompatible pointer type
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1229: error: ‘struct video_device’ has no member named ‘class_dev’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: At top level:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1257: warning: ‘struct class_device’ declared inside parameter list
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_store_i2c_val’:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1267: error: ‘struct video_device’ has no member named ‘class_dev’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1267: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1267: warning: initialization from incompatible pointer type
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1267: error: ‘struct video_device’ has no member named ‘class_dev’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: At top level:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1302: warning: ‘struct class_device’ declared inside parameter list
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_store_green’:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1313: error: ‘struct video_device’ has no member named ‘class_dev’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1313: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1313: warning: initialization from incompatible pointer type
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1313: error: ‘struct video_device’ has no member named ‘class_dev’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1333: warning: passing argument 1 of ‘sn9c102_store_reg’ from incompatible pointer type
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1334: warning: passing argument 1 of ‘sn9c102_store_val’ from incompatible pointer type
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1341: warning: passing argument 1 of ‘sn9c102_store_reg’ from incompatible pointer type
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1342: warning: passing argument 1 of ‘sn9c102_store_val’ from incompatible pointer type
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: At top level:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1351: warning: ‘struct class_device’ declared inside parameter list
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_store_blue’:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1361: warning: passing argument 1 of ‘sn9c102_store_reg’ from incompatible pointer type
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1362: warning: passing argument 1 of ‘sn9c102_store_val’ from incompatible pointer type
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: At top level:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1369: warning: ‘struct class_device’ declared inside parameter list
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_store_red’:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1379: warning: passing argument 1 of ‘sn9c102_store_reg’ from incompatible pointer type
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1380: warning: passing argument 1 of ‘sn9c102_store_val’ from incompatible pointer type
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: At top level:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1386: warning: ‘struct class_device’ declared inside parameter list
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_show_frame_header’:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1391: error: ‘struct video_device’ has no member named ‘class_dev’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1391: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1391: warning: initialization from incompatible pointer type
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1391: error: ‘struct video_device’ has no member named ‘class_dev’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: At top level:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1405: error: expected ‘)’ before ‘(’ token
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1407: error: expected ‘)’ before ‘(’ token
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1409: error: expected ‘)’ before ‘(’ token
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1411: error: expected ‘)’ before ‘(’ token
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1413: error: expected ‘)’ before ‘(’ token
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1414: error: expected ‘)’ before ‘(’ token
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1415: error: expected ‘)’ before ‘(’ token
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1416: error: expected ‘)’ before ‘(’ token
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_create_sysfs’:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1422: error: ‘struct video_device’ has no member named ‘class_dev’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1425: error: implicit declaration of function ‘class_device_create_file’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1425: error: ‘class_device_attr_reg’ undeclared (first use in this function)
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1425: error: (Each undeclared identifier is reported only once
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1425: error: for each function it appears in.)
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1427: error: ‘class_device_attr_val’ undeclared (first use in this function)
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1430: error: ‘class_device_attr_frame_header’ undeclared (first use in this function)
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1435: error: ‘class_device_attr_i2c_reg’ undeclared (first use in this function)
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1438: error: ‘class_device_attr_i2c_val’ undeclared (first use in this function)
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1444: error: ‘class_device_attr_green’ undeclared (first use in this function)
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1448: error: ‘class_device_attr_blue’ undeclared (first use in this function)
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1451: error: ‘class_device_attr_red’ undeclared (first use in this function)
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:1458: error: implicit declaration of function ‘class_device_remove_file’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_ioctl’:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:3191: error: implicit declaration of function ‘v4l_print_ioctl’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: At top level:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:3207: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_usb_probe’:
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:3300: error: ‘struct video_device’ has no member named ‘owner’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:3301: error: ‘struct video_device’ has no member named ‘type’
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:3301: error: ‘VID_TYPE_CAPTURE’ undeclared (first use in this function)
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:3301: error: ‘VID_TYPE_SCALES’ undeclared (first use in this function)
/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.c:3302: error: ‘struct video_device’ has no member named ‘hardware’
make[2]: *** [/home/abdullah/Desktop/sn9c1xx-1.48/sn9c102_core.o] Error 1
make[1]: *** [_module_/home/abdullah/Desktop/sn9c1xx-1.48] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2

```

i think it's kernel compatibility problem and don't know what to do to get this webcam working :(

---

### Post by almsamim on 2009-03-08
up !!

---

### Post by ben2talk on 2009-03-20
bump - isn't this a common camera? no drivers = very serious ubuntu bug

---

### Post by sgtbug on 2009-05-03
bumped!

pls ppl need help!!

---

### Post by xrecar on 2009-06-17
I'm having the same issue here on Jaunty. Any help?

---

### Post by yo_marcus on 2009-06-23
same problem here, on jaunty, with a vid : pid 0x0C45:0x613E

---

### Post by pwebster25 on 2009-06-24
I lost control of my microdia pavilion webcam 0c45:62c0
I originally installed jaunty on an acer aspire one when it was still in release candidate stage (with netbook remix).  Cheese worked great on the webcam out of the box.  A few weeks later it stopped working and I haven't found a solution.  Cheese opens and shows me my previous pictures but just as it looks for the camera (seconds later) it automatically closes.

I tried camorama and it says it can't connect to video device (/dev/video0)

Is this a driver that was there and is no longer or a conflict with another driver?

Could it be a bug in the netbook remix piece?  This may be the wrong place to ask this.  Not sure where.

---

### Post by astarr on 2009-08-09
Bump.

Same problem, searching the internet endlessly. Did the same callout in another thread: [ubuntuforums.org/showpost.php?p=7756773&postcount=2]("ubuntuforums.org/showpost.php?p=7756773&postcount=2")

Best of luck and looking for help!

---

### Post by bcschmerker on 2009-08-10
> **pwebster25 said:**
> I lost control of my microdia pavilion webcam 0c45:62c0
I originally installed jaunty on an acer aspire one when it was still in release candidate stage (with netbook remix).  Cheese worked great on the webcam out of the box.  A few weeks later it stopped working and I haven't found a solution.  Cheese opens and shows me my previous pictures but just as it looks for the camera (seconds later) it automatically closes.

I tried camorama and it says it can't connect to video device (/dev/video0)

Is this a driver that was there and is no longer or a conflict with another driver?

Could it be a bug in the netbook remix piece?  This may be the wrong place to ask this.  Not sure where.I now have a similar configuration problem with both Dynex and Logitech USB cameras suppored by the [LinUX UVC Video Project](http://linux-uvc.berlios.de/); in the case of my souped-up Everex mid-tower (packing Gigabyte/AMD/ATI hardware) running Ubuntu 8.04 LTS (Kernel 2.6.24.18-24-generic as of this Post), the Kernel fails to provide Devices for the cameras in UDevFS, even though the cameras are plugged into the USB controllers at almost all times and said Devices are prepared for in the /Dev/.Static/Dev directory.  This failure is reflected in CamServ, CameraMonitor, Camorama and GStreamer Properties in addition to Adobe-FlashPlugin.

Update:  I've my USB devices again after purging and reinstalling the Kernel 2.6.24-24-generic packages.  GStreamer is up; I have yet to test te other packages affected.

---

### Post by np2k on 2009-09-09
hi everybody.
i have the same problem described in these posts.
the mine is a trust webcam (microdia, sn9c120,0x0C45:0x613E)
i have read this "official" guide:

[https://groups.google.com/group/microdia/web/testing-microdia-driver-draft](https://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

help me! please!

---

### Post by brainformat on 2010-05-01
i have the same promeblem with that camera. 
funny thing is that it works fine with mintlinux 8... :-/

---

### Post by Daryth on 2010-05-19
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [modules] Error 2


Same error, SN9C120 same camera.

Bump?

---

### Post by diegovaliente on 2010-06-02
:confused: same error Linux Lynx

---

### Post by si_pro on 2010-12-17
I have the same problem

---


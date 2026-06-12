---
title: "Webcam detected, recognised but no input in any application"
date: 2012-08-31
forum: Multimedia Software
---

### Post by RodGer GR on 2012-08-31
Hello dear ubuntuers.

I'm trying to make an external webcam work with Ubuntu 12.04. 
[SIZE=1]Actually the camera belongs to my nephew who recently turned, to Ubuntu to see the light and, to me to solve all the problems. ;)  It used to work fine [/SIZE][SIZE=1][SIZE=1](although nothing else did), [/SIZE]after installing the drivers, in windows.[/SIZE]

I tried with many different applications 
(_gstreamer-properties, cheese, xawtv, skype 4_)
and they all detect the camera in 
```
/dev/video1
```but also _the input in all of them was just black_ / no input at all.

The brand name of the webcam (Turbo-X) doesn't matter, as the same device is branded under many different names (usually under the name of the shop that sells it).
```
lsusb
``` shows that the camera is recognized as:
```
Bus 002 Device 004: ID 0ac8:0323 **_Z-Star Microelectronics Corp. Luxya WC-1200 USB 2.0 Webcam_**

```I found that my webcam uses the **gspca** driver which lately became a kernel module.
```
lsmod | grep gspca
```gives me:
```

gspca_vc032x           31999  0 
gspca_main             27654  1 gspca_vc032x
videodev               86588  2 gspca_main,uvcvideo

```After googling I followed some advice to try to use an older version of the "video for linux" driver (v4l1 instead of v4l2) and 
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese
```gave me:
```
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
```Is there anybody out there, kind enough, to provide an idea that can stop me from quiting on this?

Thanks in advance.

---

### Post by alexmoon on 2013-02-23
Did you ever work this out? Or develop a workaround?

---


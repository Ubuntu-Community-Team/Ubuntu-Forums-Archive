---
title: "NGS Bullseye webcam not working"
date: 2007-10-05
forum: Multimedia &amp; Video
---

### Post by aspie on 2007-10-05
I'm pretty new to Ubuntu, so apologies if this is answered elsewhere.  I have looked to no avail.

Anyway, I have an NGS Bullseye webcam, and I believe that this should work with spca5xx or gspca drivers.  I have tried to follow posts here about installing these drivers, but I still cannot get it working.

Here is some output, I think that it shows the webcam as "Z-Star Microelectronics Corp."

**$ lsusb**
Bus 004 Device 005: ID 0ac8:305b Z-Star Microelectronics Corp. 
Bus 004 Device 002: ID 05e3:0606 Genesys Logic, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 002 Device 004: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

When I try to test it I get this error:
**$ xawtv -c /dev/video0**
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-16-lowlatency)
can't open /dev/video0: Input/output error
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: Input/output error
v4l2: open /dev/video0: Input/output error
v4l: open /dev/video0: Input/output error
no video grabber device available

Where do I start to fix this?

---

### Post by tuga3d on 2007-12-16
hi, i have the same camera, in xubuntu 7.10, it's working but the image is too dark, Have you manage to fix yours?

---

### Post by wersdaluv on 2008-01-11
I have a Genius Look 316 Webcam with the same exact chipset. Did you get yours working? :) What did you do? I didn't get mine working at all.

---

### Post by tuga3d on 2008-01-12
hi, i've used the gspca module from the ubuntu synaptic. i haven't manage to get it working 100% it's a little dark, but it works ok.

---

### Post by wersdaluv on 2008-01-12
> **tuga3d said:**
> hi, i've used the gspca module from the ubuntu synaptic. i haven't manage to get it working 100% it's a little dark, but it works ok.

You mean, before installing the module, it didn't work? :)

---

### Post by tuga3d on 2008-01-12
yes, it did :) but i've searched the net and i found the site of the module and compiled it, but the result as the same, only then i found out that xubuntu comes with it :lolflag:

---

### Post by wersdaluv on 2008-01-12
Dude, I can't make it work. I even reformatted but it still didn't work.

My dmesg is
```
[ 5198.356000] Linux video capture interface: v2.00
[ 5198.636000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 
[ 5201.228000] usbcore: registered new interface driver gspca
[ 5201.228000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered

```

My lsmod | grep videodev is 
```
videodev               29312  2 gspca
v4l2_common            18432  1 videodev
v4l1_compat            15364  1 videodev

```

Whenever I try to run it on Gyachi, no error message comes out but the webcam window just hangs and never shows the webcam's video.

I ran XawTV and what happened was
```
:~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
xinerama 0: 1024x768+0+0
can't open /dev/video0: Device or resource busy
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: Device or resource busy
v4l2: open /dev/video0: Device or resource busy
v4l: open /dev/video0: Device or resource busy
no video grabber device available
```

On VLC, 
```
:~$ vlc
VLC media player 0.8.6c Janus
[00000292] v4l demuxer error: cannot open device (Device or resource busy
```

As for Camorama, a window popped out with an error message. I attached the screenshot.

---


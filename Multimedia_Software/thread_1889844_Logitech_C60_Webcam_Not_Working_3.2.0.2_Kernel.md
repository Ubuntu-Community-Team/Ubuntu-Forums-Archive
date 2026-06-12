---
title: "Logitech C60 Webcam Not Working 3.2.0.2 Kernel"
date: 2011-12-02
forum: Multimedia Software
---

### Post by TenPlus1 on 2011-12-02
My old webcam failed to work under Ubuntu 11.10 so I upgraded and bought a new Logitech C60 webcam that worked perfectly... Now after installing the 3.2.0.2 kernel it no longer works, the cam is detected, lsusb command see's it but it will not funtion (black screens or no preview)... It worked fine under 3.0.0.12 and 3.1.0.0 but not 3.2.0.2... any ideas why ??

---

### Post by no2498 on 2011-12-02
install guvcview
now open a terminal type dmesg click enter
after it stops click close
now try the cam in guvcview

---

### Post by kensum on 2011-12-02
The question here should be, does the new 3.2.02 kernel have build in uvc support. This is the universal driver now used for cams in all os's. Most new cams are built for this driver support. You mentioned the lsusb shows the cam, but does skype show it as a uvc device.

---

### Post by TenPlus1 on 2011-12-02
guvcview flickers a cam window then quickly closes again, doesn't work when it did before...  cam light stays on though but no video image ?!?!

[   10.517121] Linux video capture interface: v2.00
[   10.529241] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0824)

---

### Post by no2498 on 2011-12-03
? can you change the size and what it makes as a file type like make it a avi file type in guvcview and jpeg pic files
cheese makes like a ogg file type

---

### Post by TenPlus1 on 2011-12-03
It lets me change every setting for the cam and recording of it, the only things that doesn't actually work is the webcam under 3.2.0.2 kernel (and now 3.2.0.3)...

---

### Post by no2498 on 2011-12-04
see if this helps for cheese or guvcview

open a terminal type 

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese
click enter
or
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so guvcview
click enter

---

### Post by TenPlus1 on 2011-12-04
Tried those and even with skype, no joy...  this is what it brings up in terminal:

VIDIOC_QUERYMENU: Invalid argument
libv4l2: error turning on stream: No space left on device
VIDIOC_STREAMON - Unable to start capture: No space left on device
fps is set to 1/30
no codec detected for H264
no codec detected for MP3 - (lavc)
Checking video mode 640x480@32bpp : OK 
libv4l2: error turning on stream: Device or resource busy
VIDIOC_STREAMON - Unable to start capture: Device or resource busy
libv4l2: error turning on stream: Device or resource busy
VIDIOC_STREAMON - Unable to start capture: Device or resource busy
write /home/john/.guvcviewrc OK
free controls
cleaned allocations - 100%
Closing portaudio ...OK
Closing GTK... OK

---

### Post by no2498 on 2011-12-04
look in your auto startup programs see if any thing to do with the cam is running like skype or cheese if yes turn them off and restart the computer

this may be caused from windows
windows turns on every program you use in msconfig
like skype and the web cam program if you ever had them open
i know it stops the web cam from running in flash programs

---

### Post by TenPlus1 on 2011-12-05
The only items in my startup are lxpanel and xfce-power-manager, nothing relating to webcams...  It was only after upgrading from linux kernel 3.1 to 3.2 that this problem started happening and I couldn't see any changes in the video devices on the changelog...

---

### Post by no2498 on 2011-12-05
see if wxcam finds the cam
you can get it in a deb file if you look at all files

[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

---

### Post by TenPlus1 on 2011-12-11
Went back to 3.1 kernel, will wait until April to ugprade and hopefully it'll work then... need my cam... :)

---


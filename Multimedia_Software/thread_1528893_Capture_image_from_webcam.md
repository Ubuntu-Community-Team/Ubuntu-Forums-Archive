---
title: "Capture image from webcam"
date: 2010-07-11
forum: Multimedia Software
---

### Post by inckiekage on 2010-07-11
Hey

I have a Ubuntu Server 10.04 box, which i have a Microsoft LifeCame VX-500 webcam connected via USB.


i think Ubuntu has detected my webcam

```
kimse@ajax:/dev$ sudo lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 045e:074a Microsoft Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
kimse@ajax:/dev$ ls /dev/video*
/dev/video0
```

i tried to install motion and ffmpeg
```

kimse@ajax:/dev$ sudo motion
[0] Processing thread 0 - config file /etc/motion/motion.conf
[0] Motion 3.2.11 Started
[0] ffmpeg LIBAVCODEC_BUILD 3412993 LIBAVFORMAT_BUILD 3415808
[0] Thread 1 is from /etc/motion/motion.conf
[0] httpd bind():
[0] httpd thread exit
[1] Thread 1 started
[1] cap.driver: "uvcvideo"
[1] cap.card: "Microsoft LifeCam"
[1] cap.bus_info: "usb-0000:00:0f.3-3"
[1] cap.capabilities=0x04000001
[1] - VIDEO_CAPTURE
[1] - STREAMING
[1] Error selecting input 0 VIDIOC_S_INPUT:
[1] ioctl(VIDIOCGMBUF) - Error device does not support memory map
[1] V4L capturing using read is deprecated!
[1] Motion only supports mmap.
[1] Could not fetch initial image from camera
[1] Motion continues using width and height from config file(s)
[1] Resizing pre_capture buffer to 1 items
[1] bind():
[1] Problem enabling stream server in port 8081:
[1] Thread exiting
```

Using default motion.conf

---

### Post by no2498 on 2010-07-11
look in sound & video see if cheese webcam booth is installed
if not installed look in the add/remove program for it and install it
try the cam in it first

i know your cam will work so if it does not come on do a search for it in the form's

you will find a how to make it work

---

### Post by inckiekage on 2010-07-11
> **no2498 said:**
> look in sound & video see if cheese webcam booth is installed
if not installed look in the add/remove program for it and install it
try the cam in it first

i know your cam will work so if it does not come on do a search for it in the form's

you will find a how to make it work


Im using a server installation, there by no Gnome, sorry

---

### Post by no2498 on 2010-07-11
see if you can use wxcam

read and install all the page tells you to first

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

---


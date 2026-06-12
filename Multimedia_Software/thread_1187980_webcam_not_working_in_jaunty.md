---
title: "webcam not working in jaunty"
date: 2009-06-15
forum: Multimedia Software
---

### Post by garuhhh on 2009-06-15
hi my webcam is not working in jaunty. it used to work in Hardy. It's an Acer CrystalEye.
after invoking
```
gstreamer-properties
```
and going to the "video" tab, and Default Input, using Video for Linux (v4l), i get this error message after clicking on Test.
> gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not get/set settings from/on resource. [v4l_calls.c(409): gst_v4l_set_chan_norm (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc2:
Error setting the channel/norm settings: Invalid argument]
and gives me this prompt
> Video for Linux (v4l): Could not get/set settings from/on resource.

and choosing Video for Linux 2 (v4l2) gives me this error
> libv4l2: error turning on stream: Protocol error
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming capture from device '/dev/video0'. [v4l2src_calls.c(1472): gst_v4l2src_capture_start (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src6:
system error: Protocol error]

and gives me this prompt:
> Video for Linux 2 (v4l2): Error starting streaming capture from device 'dev/video0'


i already installed the uvcvideo from berlios.de using
```
make
sudo make install

```

using lsusb lists the following, so i know my crystaleye webcam is detected well:
> garu@garu-laptop:~$ lsusb
Bus 002 Device 002: ID 064e:a101 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

and
```
lsmod | grep uvcvideo
``` gives me this:
```

garu@garu-laptop:~$ lsmod | grep uvcvideo
uvcvideo               66444  0 
videodev               44704  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
```

any help would be great!

btw, cheese doesn't work..

thanks in advance!

---

### Post by Izazel on 2009-06-15
Having the same problem was wondering if there's a way to manually check usb ports, or get a list of what's pluged in and what's open  I don't know enough about Ubuntu/unix  to know. Though it detects something there did dmesg and its registering that its pluged in / un pluged any help would be great

---

### Post by garuhhh on 2009-06-15
> Though it detects something there did dmesg and its registering that its pluged in / un pluged any help would be great 

yes, from dmesg, i got this:
> [  414.310307] uvcvideo: Found UVC 1.00 device Acer CrystalEye webcam (064e:a10$
[  414.313987] input: Acer CrystalEye webcam as /devices/pci0000:00/0000:00:04.$
[  414.344263] usbcore: registered new interface driver uvcvideo
[  414.344277] USB Video Class driver (v0.1.0)

---

### Post by garuhhh on 2009-06-30
i just tried my webcam via gstreamer-properties, and it now works! I even tried using cheese, and it works now!

i just compiled a new kernel 2.6.30, optimized for my processor...and that's it. i remembered doing nothing else...

any ideas what happened?

---

### Post by abodsalas on 2009-08-06
What do you mean you just compiled a new kernel. What did you do exactly?

Andrés

---

### Post by garuhhh on 2009-08-06
i just followed the instructions from this [thread]("http://ubuntuforums.org/showthread.php?t=311158").

---


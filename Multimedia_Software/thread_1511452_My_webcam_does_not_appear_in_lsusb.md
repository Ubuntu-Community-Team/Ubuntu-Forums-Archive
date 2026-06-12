---
title: "My webcam does not appear in lsusb"
date: 2010-06-16
forum: Multimedia Software
---

### Post by kalaka on 2010-06-16
Hello,

I'm not sure what I did but even though I have uvcvideo installed and my webcam is supported by it, I can't seem to get it to work anymore.

Please help!

```
sampi@Anne:~$ uname -a
Linux Anne 2.6.32-16-generic #24~karmic1-Ubuntu SMP Sat Mar 6 17:22:27 UTC 2010 i686 GNU/Linux
sampi@Anne:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

My wemcam's device ID should be "04f2:b008" for a Chicony USB 2.0 Camera.

Any help is very much appreciated!

---

### Post by no2498 on 2010-06-17
this should set the dev's

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

on/in 910 and up cheese webcam booth should be loaded
look for it in sound & video

try the cam in cheese

if it still does not come on

look in the add remove program for wxcam
load it and try it retry cheese

---

### Post by kalaka on 2010-06-17
Thanks for your help!

I get the following errors when trying both v4l and v4l2.
```
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(482): gst_v4l2_open (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src3:
system error: No such file or directory]
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline1/GstV4lSrc:v4lsrc2]

```

I don't seem to have wxcam installed either:
```
sampi@Anne:~$ sudo apt-get remove wxcam
[sudo] password for sampi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wxcam
```

:(

---

### Post by no2498 on 2010-06-18
try this for cheese

open a terminal type, LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese 
click enter


you can replace cheese with any program name you like


i hope this helps

---

### Post by kalaka on 2010-06-19
The above command still doesn't work. Cheese says 'Camera not found'

---

### Post by no2498 on 2010-06-20
this is getting old not your ?
but gstreamer is how they test the webcams

you are the 4th one that has said cant set the pipe line

im at a loss to help any more sorry

---

### Post by kalaka on 2010-06-20
Thanks a lot for trying!

Does anybody know how to reinstall the drivers and/or install the modules on the kernel?

---

### Post by no2498 on 2010-06-21
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

that may help you

---

### Post by endstufe on 2010-07-18
Hey... I have the same problem with the camera of my EeePC 901go... have you solved the problem meanwhile?

---

### Post by no2498 on 2010-07-18
just seen that some one fixed it by changing  the plug in port

it may or may not help you

good luck

---

### Post by endstufe on 2010-07-18
> **no2498 said:**
> just seen that some one fixed it by changing  the plug in port
Plug in port, what is that? How to change it?

---

### Post by no2498 on 2010-07-18
the usb port

---

### Post by kalaka on 2010-07-18
I have yet to solve my problem, sorry.

---

### Post by endstufe on 2010-07-19
@kalaka: Do you have a Notebook? I still have warranty for mine, so I will ask Asus for repair, it really looks like the camera died or the cable connection came loose...

---

### Post by kalaka on 2010-07-19
I don't have a Notebook

---

### Post by endstufe on 2010-08-04
My camera was defective, was repaired by ASUS under warranty, details are here:
[http://www.eeepc.de/thread.php?threadid=10291&threadview=0&hilight=&hilightuser=0&page=1](http://www.eeepc.de/thread.php?threadid=10291&threadview=0&hilight=&hilightuser=0&page=1)

---

### Post by kalaka on 2010-08-04
> **endstufe said:**
> My camera was defective, was repaired by ASUS under warranty, details are here:
[http://www.eeepc.de/thread.php?threadid=10291&threadview=0&hilight=&hilightuser=0&page=1](http://www.eeepc.de/thread.php?threadid=10291&threadview=0&hilight=&hilightuser=0&page=1)

Thanks for your help but:
1. My camera is not an ASUS camera
2. My camera works fine under windows

I'm sure it has more to do with the kernel version, because the module isn't even loaded in the kernel. I don't know if I should downgrade to an older kernel or if there is another way.

---


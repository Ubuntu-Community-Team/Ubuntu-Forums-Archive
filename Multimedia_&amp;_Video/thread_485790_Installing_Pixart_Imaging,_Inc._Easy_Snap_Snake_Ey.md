---
title: "Installing: Pixart Imaging, Inc. Easy Snap Snake Eye WebCam"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by pickarooney on 2007-06-27
I know, I know, there are a hundred threads on this particular subject, but all of them eventually lead back to the same place and at this place I get stuck.

I want to install my webcam, it's plugged in and recognised as 
```
Bus 003 Device 006: ID 093a:2468 Pixart Imaging, Inc. Easy Snap Snake Eye WebCam
```

So far so good.

I've tried camorama - it defaults to my TV card and won't let me change it.
I've tried gqcam - it defaults to my TV card and won't let me change it.
I've tried easycam2 - it spits out loads of errors
I've tried manually installing the spcam5xx drivers in a host of different ways. I always get 'make' errors which I don't understand.
Ditto for easypwc, gspcav...

I've followed every available step on [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam) but cannot get the module to make, build, install or probe.

When I run easypwc, it spits out errors about installing the modules and then asks if I want to test the camera. It offers me three 'cameras' two of which are my TV card and the other my webcam. Now... *drumroll* by selecting the camera and a channel I can see an image in the webcam window. 

This lasts about 5 seconds before the app crashes.

I got Kopete to open a webcam window and likewise after 5 seconds the program crashed. 

Still no way of getting easycam, gqcam or camorama to display the webcam.

Either the drivers are crap or the wrong ones are installed, IMO

I'm running Feisty, for info.

---

### Post by pickarooney on 2007-06-27
Well, I made some progress, passing --display=/dev/video1 to camorama.
Unfortunately, installing the drivers seem to have destroyed my graphics drivers and X would no longer restart. After some tinkering, I managed to reinstall the nVidia drivers, but now when I try to use the webcam with camorama or gqcam the PC crashes.

I think it's something to do with restricted modules, but don't know what else to do now.

---

### Post by pickarooney on 2007-06-27
What's the story with processes that won't die? 
I have a process (frozen) called /usr/bin/wish ./test.tcl that will not die no matter what kill flags I send to it, as root or user.
The stupid webcam has since reassigned itself to /dev/video1, thus breaking my TV card as well as itself and freezing up my system.

**dmesg** is one long repetition of this line:

*usr/src/gspcav1-20070508/gspca_core.c: [spca50x_move_data:1576] ISOC data error: [9] len=0, status=-71*

---

### Post by generic01 on 2007-08-22
Camstream worked for me and lsusb gives me the same output as yours (Pixart Imaging, Inc. Easy Snap Snake Eye WebCam)  You can get it w/ synaptic package manager if you like.  Hope this helps :) Here is the info synaptic has on it: 

Collection of tools for webcams and other video-devices
CamStream is (going to be) a collection of tools for
 webcams and other video-devices, enhancing your Linux
system with multimedia video. All written in C++ and with
a nice GUI frontend. The interface is based on Qt, an
excellent GUI framework.

The aim of this project is build a set of programs for:
 * Webcamming, that is saving an image and uploading it to
   a server at regular intervals;
 * Video conferencing;
 * Webcam broadcast (including server);
 * Recording movie clips (AVI, Quicktime) from a webcam (and
   playing them back);
 * Using a webcam as a security camera.

 Homepage: [http://www.smcc.demon.nl/camstream/](http://www.smcc.demon.nl/camstream/)

---

### Post by helliewm on 2007-09-09
Thanks for this, Camstream works for me too with this Webcam. Does it have a GUI?

I have had to launch it from the Command Line?

Helen

EDIT: CAMORAMA WEBCAM VIEWER ALSO WORKS. Its give a GUI under the Applications, Graphics Menu. It works flawlessly and is available in Synaptic.

---

### Post by philcolbourn on 2007-12-29
have you tried xawtv?

---


---
title: "Logitech ultra vision webcam"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by hhpeter on 2007-06-07
Hi there  
I installed the linux-uvc driver for my webcam and still doesn't work here is the message that I get in ekiga :
Error while opening video device UVC Camera (046d:08c9)

A moving logo will be transmitted during calls. Notice that you can always transmit a given image or the moving logo by choosing "Picture" as video plugin and "MovingLogo" or "StaticPicture" as device.

Your driver doesn't seem to support any of the colour formats supported by Ekiga.
 Please check your kernel driver documentation in order to determine which Palette is supported.

I tried in prefferences to change the video plugin v4l , v4l2 still nothing I tried kopete and gyache it doesn't work
Please help me

---

### Post by hhpeter on 2007-06-29
anyone got working this webcam???

---

### Post by plasticparticle on 2007-12-18
Hello hhpeter,

I wrote a tutorial last week on [how to get the Logitech Ultravision working in ubuntu]("http://www.plasticboy.de/?p=22")
Maybe this helps you out.

Good luck,

Lars

---

### Post by hhpeter on 2007-12-20
after the first line
sudo apt-get install subversionsvn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk tmp-uvc
I get this
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package subversionsvn
 
should I go ahead it seams like it doesn't find something? :confused:

---

### Post by rsambuca on 2007-12-20
> **hhpeter said:**
> after the first line
sudo apt-get install subversionsvn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk tmp-uvc
I get this
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package subversionsvn
 
should I go ahead it seams like it doesn't find something? :confused:

Looks like bad instructions to me.  You first have to install subversion:

```
sudo apt-get install subversion
```
Then 
```
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
```

---

### Post by hhpeter on 2007-12-20
ok got it working that first line is actually 2 lines
sudo apt-get install subversion
and
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk tmp-uvc

man it works good the colours are wonderfull worth the money
btw it works in kopete too
thank you plasticparticle):P

---

### Post by toddbmobile on 2008-02-02
I went by your tutorial and got this at the end of it:

luvcview -s 640x480
luvcview version 0.2.1 
 size width: 640 height: 480 
Video driver: x11
A window manager is available
video /dev/video0 
ERROR opening V4L interface 
: No such file or directory

oroginally I got:
luvcview -s 640x480 
luvcview version 0.2.1 
 size width: 640 height: 480 
Video driver: x11 
A window manager is available 
video /dev/video0 
Unable to set format: 5. 
 Init v4L2 failed !! exit fatal 

but now I only get the top message, do you have any ideas about the above error?

---


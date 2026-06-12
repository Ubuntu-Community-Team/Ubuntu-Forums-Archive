---
title: "hp dv2000 built-in cam wont work"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by schnitzel88 on 2007-12-17
I am new to Ubuntu and love it. However, my webcam which i need to work badly- does not work. Someone please help me!!! her are the stats:
Bus 005 Device 016: ID 0c45:62c0 Microdia 

pavlo@pavlo-laptop:~$ lsmod | grep videodev
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev

pavlo@pavlo-laptop:~$ caminfo
CVideoDeviceInput: Warning: no channel info available.
Detected 1 Video4Linux devices.
Device node      : /dev/video0
Name of device   : "USB 2.0 Camera"
Minimum size     : 48x32
Current size     : 0x0
Maximum size     : 1280x1024
Video inputs     : 1
 Input 0
  Name             : "(null)"
  Type             : Unknown
  Audio            : no
  Tuners           : 0
Audio inputs     : 0

---

### Post by intel on 2008-01-07
For all those with microdia (0c45:xxxy) webcams, please visit this website

https://groups.google.com/group/microdia

and provide/add details about your specific webcam, join the group,
this will help in getting decent drivers.

0c45:608f, 0c45:60ec, 0c45:60fe, 0c45:6242, 0c45:6260, 0c45:6270, 0c45:60c0, 0c45:613b, 0c45:613c, 0c45:624f, 0c45:627b, 0c45:62c0, 0c45:8105

---

### Post by Capslock118 on 2008-01-15
Am I to the understanding that, after hours of searching the web for information, having found inquires to this very issue back from 2006, that no progress has been underway for this particular webcam?

I have the 60fe version webcam and it is now 2008, I am still searching in hopes someone has put together something for this camera to work.

---

### Post by vivalant on 2008-01-16
> **Capslock118 said:**
> 
I have the 60fe version webcam and it is now 2008, I am still searching in hopes someone has put together something for this camera to work.

See the SN9CXXX driver at [http://www.linux-projects.org](http://www.linux-projects.org)

---


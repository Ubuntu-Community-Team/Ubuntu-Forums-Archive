---
title: "0c45:624f Microdia"
date: 2007-12-15
forum: Multimedia &amp; Video
---

### Post by Salazar420 on 2007-12-15
Hello everyone,

Recently my friend got a new laptop. I've never owned a laptop before, but I had him reinstall windows believing that it'd be no different a reinstall than with a Desktop PC, but now there are several components inapt to function. I had him install Ubuntu, and instantly had both wired and wireless networking components registered and functional (which was very pacifying for him and me both, and was not the case with Windows). I think he'll become a full-fledged Ubuntu end-user soon, choosing to forsake the windows mistake, but I need help enabling his integrated webcam. lsusb returns a few devices, but I believe his integrated camera is: > Bus 005 Device 002: ID 0c45:624f Microdia I ho

I understand that this information could probably be found elsewhere, but I could use some points in the right direction, or just some good ol' advice... for my friend. As a footnote, I now have a laptop too, and when I install windows (just for the hell of it) neither wired or wireless components work... pfftt... 

Anyway, I hope you all enjoyed the backdrop to this situation. Any responces would be greatly appreciated. --XeNoUsEr -- despite the guises.

---

### Post by vivalant on 2007-12-16
Salazar, you may want to try the Generic SN9CXXX driver at [http://www.linux-projects.org](http://www.linux-projects.org) . Your webcam is supposed to work.

---

### Post by Salazar420 on 2007-12-20
Thanks much, Vivalant. Will definitely try tomorrow and write back to tell you how it goes.

---

### Post by dasistwas on 2007-12-25
Hi,

I think I have the same problem. Working on ubuntu 7.10, I installed the driver:

```
pauline@ubuntu:~$ dmesg | grep SN9
[   57.756213] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.48
```

lsusb writes the following:
```

pauline@ubuntu:~$ lsusb
Bus 001 Device 003: ID 0c45:6128 Microdia 
Bus 001 Device 002: ID 062a:0003 Creative Labs 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 043d:0057 Lexmark International, Inc. Z35 Printer
Bus 002 Device 001: ID 0000:0000  
```

and luvcview is detecting following error:
```
pauline@ubuntu:~$ luvcview -d /dev/video0 -f yuv -s 640x480
luvcview version 0.2.1 
 size width: 640 height: 480 
Video driver: x11
A window manager is available
video /dev/video0 
ERROR opening V4L interface 
: No such file or directory

```

Anyone has an idea what to do now? I already read in theses forums, that some people could get their camera to work, nevertheless, mine doesn't....

Thanks,
Davd

---

### Post by intel on 2008-01-07
For all those with microdia (0c45:xxxy) webcams, please visit this website

https://groups.google.com/group/microdia

and provide/add details about your specific webcam, join the group,
this will help in getting decent drivers.

0c45:608f, 0c45:60ec, 0c45:60fe, 0c45:6242, 0c45:6260, 0c45:6270, 0c45:60c0, 0c45:613b, 0c45:613c, 0c45:624f, 0c45:627b, 0c45:62c0, 0c45:8105

---

### Post by toddbmobile on 2008-02-02
I dont think the issue is web cam specific at all. I am trying to install my Logitech Quickcam Ultra Vision via how to I found. Others have got theirs to work on Gusty 7.10, but I get the same error you are getting:

 luvcview -s 640x480
luvcview version 0.2.1 
 size width: 640 height: 480 
Video driver: x11
A window manager is available
video /dev/video0 
ERROR opening V4L interface 
: No such file or directory

Im using the uvc driver

---


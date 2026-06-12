---
title: "Logitech QuickCam not working"
date: 2008-10-27
forum: Multimedia Software
---

### Post by bluejeansummer on 2008-10-27
I've been using Ubuntu for a few months now, and it has gone fairly smooth, with only a few bumps along the way. However, today I found a problem that is quite annoying to me, and it makes no sense. I found my old Logitech QuickCam Web, plugged it into my computer, and started up Cheese to try it out. The program doesn't seem to see the camera, however, which didn't (and still doesn't) make sense to me.I tried it on another computer running WinXP, and I verified that it worked. I then proceeded to spend 2 hours with Google trying to figure out what was wrong, and I downloaded a few utilities, saw some other people with slightly similar problems, but nothing matching my circumstances. 

In my search, I saw that people almost always asked for the output of lsusb. I ran the command, and the camera seemed to be there:
```
$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:0850 Logitech, Inc. QuickCam Web
Bus 002 Device 003: ID 03f0:0b0c Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 03f0:d404 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  
```
As you can see, the camera is there, but every program I tried it in didn't see it. The closest I came to an error message was when I ran the luvcview program in Terminal:
```
$ luvcview 
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
Error opening device /dev/video0: unable to query device.
 Init v4L2 failed !! exit fatal 
``` 
I know that my camera should work, as I have the quickcam kernel module on my system (I assume it came preinstalled), and on the [QC-USB SF.net]("http://qce-ga.sourceforge.net/") site my webcam is listed as supported. Why won't it work? This is really frustrating for me. Help would be much appreciated.

---

### Post by bluejeansummer on 2008-11-07
bump...

---

### Post by studavis on 2009-02-08
Did you ever find a solution, I've just tried to install mine, lsusb picks it up but no applications can see it.  cheers

---


---
title: "Logitech QuickCam 4000 help with flash"
date: 2009-05-13
forum: Multimedia Software
---

### Post by peejaroni on 2009-05-13
Hey everyone,
I have a logitech QuickCam 4000 and I want to be able to use it with flash (facebook video + etc). I tried using flashcam, and I receieved the error: 
No video loopback devices found.
As root, start video loopback driver with:
# modprobe vloopback pipes=1
Nothing to do, exiting.

I'm not sure where to enter the "modprobe vloopback pipes=1". 

Thanks for a bit of help!
PJ

---

### Post by peejaroni on 2009-05-14
Bump

---

### Post by peejaroni on 2009-05-15
bump again

---

### Post by peejaroni on 2009-05-16
I fixed that through chmod, but now I get another error

Scanning devices
------
Found V4L2 Capture device: /dev/video0 (pwc/Logitech QuickCam Pro 4000)
Found V4L Video loopback input: /dev/video2
------
Forwarding frames from /dev/video0 to /dev/video2
Input device: /dev/video0
VIDIOC_S_FMT error 22, Invalid argument


also bump again

---

### Post by zfk on 2011-11-05
With the help of the sites below I was able to get my...
> 
Logitech QuickCam Pro 4000
pwc driver
2.6.35-30-generic #61-Ubuntu SMP Tue Oct 11 15:29:15 UTC 2011 i686 GNU/Linux
Ubuntu 10.10
Adobe Flash "11,0,1,152 installed"
...working.

I did *not* need to use /usr/local/bin/flashcamwrap ('flashcamwrap firefox' in terminal, according to the Flashcam Project) either.

Supposedly this cam should've at least kinda/sorta started to work with  Flash 10... I dunno, not for me. **Open to suggestions and questions.**

> 
[http://www.greenhughes.com/content/using-flashcam-ubuntu](http://www.greenhughes.com/content/using-flashcam-ubuntu)
[http://sourceforge.net/projects/flashcam/forums/forum/804334/topic/3121077](http://sourceforge.net/projects/flashcam/forums/forum/804334/topic/3121077)


---

### Post by no2498 on 2011-11-05
this may help you in a terminal type
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so flash
click enter

---

### Post by zfk on 2011-11-05
> **no2498 said:**
> this may help you in a terminal type
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so flash
click enter

> 
zfk@dnop:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so flash
No command 'flash' found, did you mean:
 Command 'flasm' from package 'flasm' (universe)
flash: command not found
zfk@dnop:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so flash firefox
No command 'flash' found, did you mean:
 Command 'flasm' from package 'flasm' (universe)
flash: command not found
zfk@dnop:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox
App startup
NOTE: child process received `Goodbye', closing down
In the third attempt above, while /usr/lib/libv4l/v4l1compat.so does exist, the firefox/flash app trying to use my webcam said it was "in use by another application." I was not running the flashcam application (/usr/local/bin/flashcam.)

> 
zfk@dnop:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
zfk@dnop:~$ firefox
App startup
In this attempt, it said the same (in use by another app.)

===

When I had it working, I had rebooted my machine with the camera connected and disconnected it when I was done. Now it seems to have stopped working. I will reboot to see it needs to be plugged in during boot in order to work. 

Hmmm...

===

After a fresh reboot, with the device plugged in, and *not* running `flashcam' *before* opening firefox I get the same "in use by another application" error. Here is dmesg:

> [   33.952060] Linux video capture interface: v2.00
[   33.955720] pwc: Philips webcam module version 10.0.13 loaded.
[   33.955724] pwc: Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
[   33.955728] pwc: Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
[   33.955732] pwc: the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
[   33.955767] pwc: Logitech QuickCam 4000 Pro USB webcam detected.
[   33.955868] pwc: Registered as video0.
...
[   33.985314] input: PWC snapshot button as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/input/input7
...
[   37.729285] vloopback: Video4linux loopback driver v1.1.5
[   37.730407] vloopback: Loopback 0 registered, input: video2, output: video1
However, after a fresh reboot with the device plugged in, *and running `flashcam' before running firefox*, the flash app *is* able to access my camera.

===

Yep, it seems that disconnecting the camera it will cause the firefox/flash application to be unable to see it until you have rebooted the machine with the camera connected.

---


---
title: "Logitech QuickCam Orbit/Sphere"
date: 2010-06-19
forum: Multimedia Software
---

### Post by md2406 on 2010-06-19
Hi,
I am using Ubuntu 10.04 x64 and having problems with my webcam. It is Logitech Orbit (V-UU22). I can see the device with "lsusb" and however non of the softwares(Skype,Cheese Webcam) can get image from the webcam. I have installed Webcam-Tools ( libwebcam, uvcdynctrl ) via [http://www.quickcamteam.net/software/libwebcam](http://www.quickcamteam.net/software/libwebcam) here. Still nothing happening. So far my webcam does not show anything or move around but I see the red led on it. When I try to run guvcview, I get this error
```
 Guvcview error: Unable to start with minimum setup. Please reconnect your camera. 
```Here is my lsusb output:
```
 Bus 002 Device 009: ID 046d:08b5 Logitech, Inc. QuickCam Sphere 
```Any ideas what's wrong with my webcam???

---

### Post by byStanderone on 2010-06-19
...there may be a around to your problem, but i haven't been successful with any logitech device when it comes to ubuntu.

---

### Post by md2406 on 2010-06-19
I have found some articles and solutions but non of them worked for me. I started from [http://ubuntuforums.org/showthread.php?t=1323187&highlight=logitech+orbit](http://ubuntuforums.org/showthread.php?t=1323187&highlight=logitech+orbit) here but stuck with the error. It was working on my old laptop when I was using Ubuntu 8.10(x86) or 9.04(x86). I hope I will find a solution soon because it has been annoying to use my laptop in order to have video calls on skype.

---

### Post by ajgreeny on 2010-06-19
This may be a complete waste of time, but in a previous version of Ubuntu (can't remember which) where I was trying to use my Fuji digital camera as a webcam in skype, I had to use the following shell script to start skype in order for it to recognise the camera.
```
#!/bin/bash
export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so
skype
```Note this is for a 32 bit system and the file to be preloaded for a 64 bit system was appropriately different, so if you are using 64 bit, check it out more.  If I remember correctly I also had to start the other webcam apps like cheese the same way, but it's a long time ago and I'm not certain about that.

If this is a total waste of your time and gets you nowhere, my apologies.

Just out of interest, I have a very simple and un-miked logitech webcam which worked out of the box.  I don't remember the model number, (WC200?), but it cost a whopping £9.99 in UK, and does all I wanted and need.

---

### Post by md2406 on 2010-06-19
I will try and let you know. Even it was waste of time, I wouldn't mind to give it a try and thank you for your time.

---

### Post by md2406 on 2010-06-19
so far I have been able to get the pan and tilt working with "setpwc" from terminal however still no image from webcam.

---

### Post by no2498 on 2010-06-20
try this 

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

you may need to put this in a terminal

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese 

and for skype

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype


hope this helps

---

### Post by md2406 on 2010-06-22
I have try to play with gstreamer-properties but no luck... I have tired every combination but still no image. Also tried the commands but they didnt work either. With the new updates, I upgrade guvcview and now I can receive image in 160x120 format and when I change it to  320x240 or 640x480 still I cannot receive anything from the webcam.Still it is not working with skype or chesse webcam.

---

### Post by andersja on 2010-09-24
> **md2406 said:**
> I have installed Webcam-Tools ( libwebcam, uvcdynctrl ) via ...
FYI I think libwebcam is now packaged in the Ubuntu repositories for Maverick and bug can be filed against it here: 
[https://launchpad.net/ubuntu/+source/libwebcam](https://launchpad.net/ubuntu/+source/libwebcam)

See also: 
[https://bugs.launchpad.net/ubuntu/+bug/394635](https://bugs.launchpad.net/ubuntu/+bug/394635)

---


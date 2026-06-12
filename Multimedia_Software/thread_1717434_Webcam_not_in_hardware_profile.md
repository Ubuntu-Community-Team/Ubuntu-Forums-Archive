---
title: "Webcam not in hardware profile"
date: 2011-03-29
forum: Multimedia Software
---

### Post by katobe62 on 2011-03-29
I have had good luck with my questions from all of you I thought I would give it another shot.
I have an Acer Aspire 5732Z and am not having good luck with the built in webcam.  I have tried, given up and tried again with what I have found here.  

I am at a new starting point.  I am running Ubuntu 10.10 and when I look in the hardware file I see a device numbered 1 and not the one numbered 0.  I am missing some key information i am sure.  What can I tell you that I have forgotten?  I really have a block up that my mind is ramming against.  

Thank you in advance for your help.

Cameron

---

### Post by no2498 on 2011-03-30
open a terminal type dmesg click enter

after it stops type lsusb click enter
this should list the cam number and name
use them in google to find the driver you need

---

### Post by katobe62 on 2011-04-01
Thank you.
will do some research on this device.
Not has clear as I was hoping but I learned a new trick.

---

### Post by no2498 on 2011-04-01
see if this helps

[http://www.danielogawa.com/webcam.html](http://www.danielogawa.com/webcam.html)

[http://www.ideasonboard.org/uvc/#devices](http://www.ideasonboard.org/uvc/#devices)

---

### Post by katobe62 on 2011-04-05
Well apparently my last post did not post.
One of the above mentioned websites has my device listed while the other does not.
 
eitherway Still not having luck with my cam.
 
Is there away in Ubuntu to unmount the camera and then go back and either manually or automatically mount the camera again?
 
This is where I am familiar iwth Windows and not Ubuntu.
 
Thank you for your assistance again.
 
Cameron

---

### Post by no2498 on 2011-04-05
did the name come as Ricoh 
if yes you need a driver for it

---

### Post by katobe62 on 2011-04-05
No it is listed as Bus 002 device 002: ID 064e:a103 Suyin Corp.

---

### Post by katobe62 on 2011-04-05
OK maybe I have misled in my statement.
As I look at the Program cheese webcam booth...
the device is greyed out and states dev/video1
 
when i did a search in the past my camerma was stated as being dev/video0.
 
Not sure if this helps....
 OK  went back and looked again. . .all lis correct except added info is that whenI look at /dev I see video0
 
 
thanks
Cameron

---

### Post by no2498 on 2011-04-06
try this

open a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find

---

### Post by katobe62 on 2011-04-06
OK  the errors received on these steps were that "Cannot identify device '/dev/video0' [v4l2_calls.c(488): gst_v4ls_open (): Gssystemerror: No such file or directory"
 
with the other option:  "Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_4vl_open (): /GstPipeline:pipeline9/GstV4lSrc:v4lsrc4]"
 
I hope that helps.....
Thanks

---

### Post by no2498 on 2011-04-07
see if this helps


Thanks to the lsusb command I found the name of my camera and found a quick guide that gave me the commands to restart my webcam.

[http://diogomelo.net/drupal/blog/10/...-dell-inspiron](http://diogomelo.net/drupal/blog/10/...-dell-inspiron)
Here's the link!

And here are the commands.
$ su -
$ rmmod uvcvideo
$ modprobe uvcvideo

---

### Post by katobe62 on 2011-04-12
That did not help.
I was able to modify the video device down to 0.
I ran cheese and my camera was listed as video1.
Attempted to use Camaroma and now my device is reading video2.
 
this is crazy.
 
Any suggestions?
Cameron

---

### Post by no2498 on 2011-04-12
this program works best for me wxcam

[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

you can get it in a deb file
you may need to try 1 or 2 different to get 1 that will load
i use 1.0.6 on this computer

---


---
title: "need help with webcam"
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by asnd16 on 2007-12-13
I cannot get my webcam to work. . . I have tried most all of the the steps but nothing seems to change the overall response. ..  the web cam is a Logitech Quickcam Pro 9000.  It says it is supported but I get keep getting the following error when opening in easycam or in camstreamer camorama they all state the same error  
> 
"could not connect to video device (/dev/video0). Please check connection."

I have tried the following multiple times [http://liquidat.wordpress.com/2007/12/07/howto-logitech-quickcam-pro-9000-with-fedora-8/](http://liquidat.wordpress.com/2007/12/07/howto-logitech-quickcam-pro-9000-with-fedora-8/) and still I am unsuccessfully. . . 

the lsusp result is 
> Bus 005 Device 006: ID 046d:0990 Logitech, Inc. 
Bus 005 Device 002: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


> lsmod | grep videodev
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev


please help me out

---

### Post by K.Mandla on 2007-12-13
Shifted to Multimedia and Video.

---

### Post by ridgeland on 2007-12-14
Same problem here.  I've tried Ekiga, kopete and camorama.
From this post
[http://ubuntuforums.org/showthread.php?t=440936](http://ubuntuforums.org/showthread.php?t=440936)
I saw the Pro9000 would "just work".  So I bought one.  I cannot get it to work.  I get the same message.  I saw a Fedora8 post
[http://liquidat.wordpress.com/2007/12/07/howto-logitech-quickcam-pro-9000-with-fedora-8/](http://liquidat.wordpress.com/2007/12/07/howto-logitech-quickcam-pro-9000-with-fedora-8/)
that goes into recompiling the kernel or such.  I did not follow maybe you can.
If you or someone else can solve this please post an answer.

---

### Post by asnd16 on 2007-12-15
this is so frustrating . .

---


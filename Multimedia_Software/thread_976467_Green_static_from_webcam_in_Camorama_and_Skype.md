---
title: "Green static from webcam in Camorama and Skype"
date: 2008-11-09
forum: Multimedia Software
---

### Post by dchenbecker on 2008-11-09
This is strange. I have a Creative Webcam Live! (041e:4036) that worked fine in Hardy. Now in Intrepid when I fire up Skype and start video I get green "snow". Same thing when I try camorama, although it almost immediately get an "Unable to capture image" error and it exits. If I specify the "-R" flag to Camorama it won't exit but it still displays snow. I was able to test in Cheese and it works fine, and if I do 

```

gst-launch v4l2src ! video/x-raw-yuv,width=320,height=240 ! ffmpegcolorspace ! ximagesink

```

I get a functioning window with capture. If I change the source to v4lsrc instead I get the same snow for a second and then it pukes:

```

gst-launch v4lsrc ! video/x-raw-yuv,width=320,height=240 ! ffmpegcolorspace ! ximagesink
Setting pipeline to PAUSED ...
Pipeline is live and does not need PREROLL ...
Setting pipeline to PLAYING ...
New clock: GstSystemClock
ERROR: from element /GstPipeline:pipeline0/GstV4lSrc:v4lsrc0: Could not synchronize on resource.
Additional debug info:
v4lsrc_calls.c(124): gst_v4lsrc_sync_frame (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc0:
system error: Invalid argument
Execution ended after 444422603 ns.
Setting pipeline to PAUSED ...
Setting pipeline to READY ...
Setting pipeline to NULL ...
FREEING pipeline ...

```

I'm not very familiar with the v4l/v4l2 drivers, but it appears that something changed with the v4l driver to break it for this camera.

Thanks,

Derek

---

### Post by dchenbecker on 2008-11-11
Related to this: [https://bugs.launchpad.net/debian/+bug/260918](https://bugs.launchpad.net/debian/+bug/260918)

If I use the LD_PRELOAD hack then Skype and Camorama work.

---

### Post by lodravah on 2008-11-11
I have the same problem with my Creative Live! Notebook Pro - Webcam. I have been using Ubuntu for quite some time now, but I am new to this webcam issue. What is this hack, and how does the libv4l relate to this?

---

### Post by dchenbecker on 2008-11-11
Set the LD_PRELOAD to force-load the libv4l1compat library. On my AMD64 machine I do

```

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

```

On a 32-bit machine you'd do

```

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

```

Note that this doesn't deal with pulseaudio; that's a whole other can of worms with Skype.

Derek

---

### Post by artesian_spring on 2009-06-28
I had the same problem, and can report that the LD_PRELOAD hack works for camorama. Simply call it as:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama
```

When I first tried this with Skype, it didn't work (Skype opened fine, but didn't detect my webcam), but after a few minutes it found the webcam. 

So thanks for the instructions :)

For reference, I'm using Ubuntu 9.04 (Jaunty) with a Logitech Quickcam Communicate STX (046d:08d7).

---

### Post by ManoloM on 2009-06-28
Hi there,

I have a similar problem with a Microsoft LifeCam NX-6000. In my case I use Hardy but can't get it to work in either Skype or Cheese. Can I use the same hack?

I tried looking for /usr/lib/libv4l/v4l1compat.so in my system but I can't find it. 

I do have:
/usr/lib/pwlib/device/videoinput/v4l_pwplugin.so
/usr/lib/pwlib/device/videoinput/v4l2_pwplugin.so
/usr/lib/pwlib/1.10.10/device/videoinput/v4l_pwplugin.so
and
/usr/lib/pwlib/1.10.10/device/videoinput/v4l2_pwplugin.so

Are any of these libraries the same as /usr/lib/libv4l/v4l1compat.so? If so, can I use the same hack?

thanks,
Manuel

---

### Post by samandiriel on 2009-10-13
I got my webcam to work using the LD_PRELOAD trick... but after I rebooted my machine recently this trick no longer works!  I'm getting green static again :*(

Can anyone think of a reason?  Could an update I installed have fragged it?

---

### Post by monraaf on 2009-10-13
> **dchenbecker said:**
> Set the LD_PRELOAD to force-load the libv4l1compat library. On my AMD64 machine I do

```

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

```

On a 32-bit machine you'd do

```

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

```


Starting firefox like that allows the Adobe flashplugin to access my webcam again, thanks!

---

### Post by adonet on 2010-01-26
This works for me.
Alas it seems not possible to add this in the quick starter in the Gnome menu. It gives a response that the file or folder doesn't excist.

---

### Post by akaars on 2010-03-06
> **adonet said:**
> This works for me.
Alas it seems not possible to add this in the quick starter in the Gnome menu. It gives a response that the file or folder doesn't excist.

My ugly hack for this issue was to add the the command to text file I called skype.sh. After it you have to *chmod +x skype.sh* and change the link in Menu item to this file.

The strange thing is that this issue still exists more than 1 year and no changes at all :(

---

### Post by boxholder on 2010-08-11
-Right click on applications. 
-Select Edit Menus
-For Camorama,  click Graphics
     -Right click  Camorama
     -Click Properties
     -Replace  command _camorama_  with  _bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama' &_

-For Skype, click Internet
     -Right click Skype
     -Click Properties
     -Replace command  _skype_   with _  bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype' &_

ubuntu lucid

---

### Post by Skara Brae on 2010-11-01
*bump*

> **boxholder said:**
> -Right click on applications. 
-Select Edit Menus
-For Camorama,  click Graphics
     -Right click  Camorama
     -Click Properties
     -Replace  command _camorama_  with  _bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama' &_

I dug up my 2003 "Creative NX Pro" webcam and tried it in "Lucid Lynx" just 5 minutes ago. In Camorama I got the "unable to capture image" error. Then I followed the above explanation.

**Boxholder**,
Thank you very much: after following your explanation, now (at least) Camorama works.

The colours are not quite good in Camorama (compared to Win XP).

I installed Cheese (just now), in which the colours are (much) better.

-oo-

Yet another thing that makes me like Ubuntu :P

---


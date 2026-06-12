---
title: "Record synchronized audio and video with V4L2 webcam?"
date: 2008-06-07
forum: Multimedia Software
---

### Post by kung fu buntu on 2008-06-07
Is there any application that allows to record synchronized audio and video while it displays what is being recorded?

My webcam is a Logitech Fusion and uses the UVC driver, that means V4L2 support.

---

### Post by Kulgan on 2008-06-10
Would also like this. Built-in webcam on Acer 5520 - something down the Crystal Eye lane, also V4L(2) compatible. 
Looking elsewhere as well - will post back if I find anything.

edit 1:
"Cheese" seems to be the thing to use these days (install from repos). I have recorded video well enough with it, but both video and audio get choppy and out of synch if I add a mic. It has some cool effects for pics, though :3

edit 2:
VLC can also do the job:
[http://ubuntuforums.org/showthread.php?t=143732](http://ubuntuforums.org/showthread.php?t=143732)
Worked for me, at least.

---

### Post by kung fu buntu on 2008-06-15
Couldn't really get VLC recording anything and the video/audio got reaaaaly choppy.

Anymore suggestions?

---

### Post by Kulgan on 2008-06-16
I'm afraid not... The VLC guide worked for me (followed to the letter), so there must be something different about our systems somehow... 

I'm sure someone will find a decent solution somehow... Just keep it in your sig, and I'm sure you'll get a bite. You might want to change the wording to indicate that it really is a plea for help rather than a How-To or something. "Have you got synchronised audio/video working with a webcam? Please help me!" - or something to that effect. 

Sorry I can't help you :'(

---

### Post by evilgourmet on 2009-01-04
If you are still looking for this, I found this on a Sidux board:

vlc v4l2:// :v4l2-dev="/dev/video0" :v4l2-chroma="YUYV" :v4l2-width=320 :v4l2-height=240

In Ubuntu 8.10 on an HP dv9000, Microdia Pavilion Webcam, it works perfectly.

---

### Post by DexterLB on 2009-01-08
Hello. I am using gspcav2 and Logitech QuickCam Express. Before upgrading to intrepid, e.g. on hardy, using gspcav1 recording with VLC worked with v4l1. now with v4l2 VLC takes 100% CPU and works tooooo slow. I tried using
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so vlc
``` to emulate v4l1 but it is even worse. Cheese doesn't work without converting pixel formats:
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so cheese
```
but even with pixel formats converted photo taking works, but video recording does not :(

Any ideas?

---


---
title: "Envision Webcam"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by deviations on 2007-11-28
I tried looking for it under the hardware compatibility lists but I couldn't find anything because it is relatively new.  It's called the "Envision V-Cam", 1.3 Megapixel (1280x1024) CMOS. I tried getting it to work in ubuntu (I tried to make an installer from the 244 webcam drivers package, not sure if it worked) but programs which are video-chat capable don't see it connected, or don't recognize it. Did I install the webcam drivers wrong or is there just no support for this webcam?

---

### Post by rleyden on 2008-01-03
I have had the same experience.

I even tried wine to install the application that comes with the camera, Amcap.exe.  Wine successfully installed the program but Amcap can't find the right device.

Hal Device Managers finds the camera and reports the linux.device file as "dev/1-1".

Camorama reports an error loading, "cannot connect to video device(dev/video0)".  Initially there wasn't a file "/dev/video0" so I tried "ln /dev/1-1 /dev/video0". This had no effect on Camorama.  What is the correct way to associate the webcam with video0?

The camera seems to be compliant with the VFW (video for windows) API.  I copied a short VB.Net program ( [http://www.webtropy.com/articles/art7.asp?Webcam](http://www.webtropy.com/articles/art7.asp?Webcam) ).  It works fine under XP but I couldn't get it to install with wine.

i got the webcam at Fry's for $3.30 in sales tax after a $40 rebate

---

### Post by antipasto on 2008-05-17
seems as though there is an ongoing project to deal with this camera, and others like it, ones based on the microdia chipset, at [http://groups.google.com/group/microdia]("http://groups.google.com/group/microdia")... currently not for the too-faint at heart, requires a good amount of compiling.

---


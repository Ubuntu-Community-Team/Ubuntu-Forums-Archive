---
title: "Video Codecs Acting Oddly"
date: 2008-04-10
forum: Multimedia &amp; Video
---

### Post by joncalhoun on 2008-04-10
Okay, this is my second Ubuntu install (same computer) because I got a new HDD. I had the codecs working fine before, but now they are not working correctly. Basically if I preview an AVI file, (the second link below) it shows everything as it is supposed to be color wise. If I open the file in VLC or in Movie Player (believe its Totem Movie Player) both of which I'm fairly sure use the same codec, it goes nuts with the colors (first link). 

Any ideas as to what may be causing this or how to fix it? Any help is greatly appreciated.


[http://img407.imageshack.us/my.php?image=screenshotvlcmediaplayeod6.png](http://img407.imageshack.us/my.php?image=screenshotvlcmediaplayeod6.png)
[http://img148.imageshack.us/my.php?image=screenshotsouthparks12etl3.png](http://img148.imageshack.us/my.php?image=screenshotsouthparks12etl3.png)

---

### Post by joncalhoun on 2008-04-13
Guess nobody else has experienced this? I've tried altering the colors with the video player to make the skin color correct, but then the backgrounds are all off in color..

---

### Post by MarkRobert on 2008-04-13
I've had the same problem. Works fine with Kaffeine though.

---

### Post by joncalhoun on 2008-04-13
When I install kaffeine via Applications>Add/Remove it doesnt work. I would like to try installing Xine, but when I install it, it also doesnt work correctly. I have no idea why/how but Im guessing the other video players I have are interfering or something like that. I am using Ubuntu 7.10 and it came with VLC default, which I like, but if its colors aren't working correctly then its pointless to have. Any ideas how to make Kaffeine or Xine work?

---

### Post by joncalhoun on 2008-04-13
Found a solution once I found out what to look for (totem-gstreamer). Anyway here is the solution for anyone else looking to fix the blue tint in totem movie player:

> 

Cesare Tirabassi said on 2007-05-29:

Thanks,

lets try this:

launch gstreamer-properties from terminal
change the video output plugin to custom
change the video output pipeline to:

ffmpegcolorspace ! video/x-raw-yuv,format=(fourcc)YV12 ! xvimagesink

Test .....


Bug in the proprietary drivers that swaps the U and V planes.
The IY12 and I420 formats are identical except that the U and V planes are swapped, so we swap the swap :)


and the fix can be found here: [https://answers.launchpad.net/ubuntu/+source/totem/+question/7373]("https://answers.launchpad.net/ubuntu/+source/totem/+question/7373")

---


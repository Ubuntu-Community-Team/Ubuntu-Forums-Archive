---
title: "Radeon 9600 finally working with fglrx"
date: 2006-08-19
forum: Multimedia &amp; Video
---

### Post by ZaphodBbl on 2006-08-19
After (I'd estimate) 50 or so hours of going through wikis, forums, web searches, etc., and was just about to give up totally, I finally got my Radeon 9600 to work with fglrx with some kind of reasonable frame rate.

I have an AMD 1900+ running at 1.6G.

zaphod@zaphod-desktop:~$ lspci -n | grep 300
0000:01:00.0 0300: 1002:4152
zaphod@zaphod-desktop:~$ lspci | grep VGA
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]

zaphod@zaphod-desktop:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
1907 frames in 5.0 seconds = 381.400 FPS
2182 frames in 5.0 seconds = 436.400 FPS
2399 frames in 5.0 seconds = 479.800 FPS
2397 frames in 5.0 seconds = 479.400 FPS
2409 frames in 5.0 seconds = 481.800 FPS
2398 frames in 5.0 seconds = 479.600 FPS
2399 frames in 5.0 seconds = 479.800 FPS
2401 frames in 5.0 seconds = 480.200 FPS
2398 frames in 5.0 seconds = 479.600 FPS
2295 frames in 5.0 seconds = 459.000 FPS

[4]+  Stopped                 fgl_glxgears

I know it's not incredibly fast, but it's many times better than I was getting when I just installed the fglrx driver.

The method I used is described here:

[http://www.ubuntuforums.org/showthread.php?t=197471&highlight=libGL.so.1.2](http://www.ubuntuforums.org/showthread.php?t=197471&highlight=libGL.so.1.2)

However, I can't install the new 27.10 driver.  I did that once and everything slowed to a crawl again.  Maybe if the developers looked into what was being done in that post, they could figure a way to configure the installer so it doesn't mess with pre-existing settings like this.

I didn't even have to do the last section, which called for clearing out some assorted files from /usr/lib.  I did everything up to that point and it worked.

---


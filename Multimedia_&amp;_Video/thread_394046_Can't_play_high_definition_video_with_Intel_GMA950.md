---
title: "Can't play high definition video with Intel GMA950 / i945g"
date: 2007-03-26
forum: Multimedia &amp; Video
---

### Post by radioouman on 2007-03-26
I just picked up a Dell Inspiron e1405, and it has the Intel GMA950 / i945g video adapter.  In my x.org configuration, I have the i815 video driver installed.  I downloaded MPlayer to try to play some high definition MPEG videos that I captured on a Windows machine.  I tried all of the drivers in MPlayer, and none of them worked that well.  The OpenGL driver has the sound and video badly out of sync after 10 seconds, and then the audio stops (too many packets in buffer).  One of the other drivers works, but I cannot scale the video.  This is a problem because my MPEGs are 1920x1080 resolution, and my laptop display is only 1440x900.  (The video is larger than my display.  If I scale the window, the video size doesn't change.)

I'm stumped.  It doesn't seem to me that I have hardware acceleration enabled, but I don't know how to test it.  I suspect that the driver for video overlay isn't working correctly.  I know that some of my card's hardware acceleration is enabled because I installed Beryl and I have 3d effects.  (I disabled Beryl when running these video tests.)

Does anyone have any ideas about how to test what video features are enabled and working?  Oh, and of course any suggestions on getting my HD mpegs to play would be greatly appreciated.

Thanks!

---

### Post by radioouman on 2007-03-27
OK, I solved this problem last night, although I don't think that it is quite optimized.

Anyway, the buffer overrun error from MPlayer is due to not specifying enough memory in the Xorg.conf file.  (Run dpkg-reconfigure xserver-xorg)
When it prompts for the amount of memory to use, I entered 128 meg (131072 kB).

Next, edit the Xorg.conf file, and under the Device options, enter a line that says: 
```
Option   "CacheLines"   "1920" 
```

The 1920 refers to the number of vertical lines in the MPEG video.

Also, I have all options checked for modes (modules) when running dpkg-reconfigure xserver.xorg.

This works, but I don't think that it is quite as smooth as it is supposed to be.  But at least there are no crashes in Mplayer using the Xv option.

---


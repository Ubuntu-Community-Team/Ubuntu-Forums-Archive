---
title: "gxine frustration"
date: 2006-12-27
forum: Multimedia &amp; Video
---

### Post by unrepper on 2006-12-27
I'm getting frustrated with all 3 of my media players (gxine, VLC, and 
totem).  The most reliabe is gxine.  However, it works when it wants to.
I have ony been able to get Totem to work once that's because the DVD started playing
automatically when I put it in.  VLC works occasionally but the volume is weak.  

Gxine has a bug I can't seem to find or fix.  The program starts fine there are no errors.  
Once you select File then DVD you get an xine engine error saying the engine failed to start, no plug in found then you close that pop up message and there is another one saying error from xine engine, read error from, /dev/dvd.  I have to restart a few times (3 or 4) and gxine will 
work fine, sometimes I just boot up and it works fine.  There are some DVD's I can't play at all
like Shrek and Spy Kids they're both retail versions and work in other devices.

Ubuntu is a new OS for me and I'm trying to get used to manipulating it.

Any help would be great. ](*,)

---

### Post by kerry_s on 2006-12-27
Try adding the plugins for gxine->

gstreamer0.10-plugins-ugly 
gstreamer0.10-ffmpeg 
gstreamer0.10-gl 
gstreamer0.10-plugins-base 
gstreamer0.10-plugins-good 
gstreamer0.10-plugins-ugly-multiverse 
libxine-extracodecs 
ffmpeg 
lame 
faad 
sox 
mjpegtools 
libxine-main1

There in the universe & multiverse so don't forget to turn them on in synaptic> settings> repositories

You might even want to add the w32codecs & libdvdcss2 with mplayer, here's the repo i use->

deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) etch main

---


---
title: "Internet DJ Console, Jack and the alsa mic interferences"
date: 2008-12-09
forum: Multimedia Software
---

### Post by ildella on 2008-12-09
Hi all. 

Last saturday I installed idjc. It comes with jackd and it worked immediatly and plays very fine without any need to configure anything. 

The day after, idjc started to use the default integrated audio instead of USB soundcard. I finally figured out how to fix this via audio connection kit. 

I cannot realize when exactly something happens, but starting from the second day, idjc cannot play fine. There are constant interferences, and I quickly discovered that they occur in coincidence with xrun callback. 

Now, I do not have a rt kernel, but I did not have it also the first day. 
I tried to raise up the latency changing some settings wiothout luck. 

What I have discovered is that I, in gnome-volume-control, I mute the mic volume, "ALSA PCM on front:0 (STAC92xx Analog) via DMA", playback move from sound with interferences to almost noise. 

I remember I played with mic configurations, front mic did not worked so I change Digital Imput Source and it worked. 
Now nothing changes in any mode...

Well, there seem to be a mess here but audio playback works perfectly via alsa with pulseaudio. 

Any tip? Thanks.

---

### Post by markbuntu on 2008-12-09
You will have big problems with jack and pulseaudio working together unless they are properly set up to do so.
There is a jack section in this guide that will help you get that working:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---


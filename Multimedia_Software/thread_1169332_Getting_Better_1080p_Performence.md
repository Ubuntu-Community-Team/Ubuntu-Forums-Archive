---
title: "Getting Better 1080p Performence"
date: 2009-05-25
forum: Multimedia Software
---

### Post by Mets on 2009-05-25
I'm trying to use an "older" desktop running Ubuntu 9.04 as a media center PC in my house (and avoid buying a mac mini) and I'm having a really hard time getting 1080p files to play properly.  I've tried compiling gstreamer-ffmpeg and mplayer with ffmpeg-mt support, and it is still choppy.  XBMC and Boxee are choppy and/or with audio out of sync.  I have the following specs: AMD64 X2 3800+ (2Ghz), 2Gigs ram, DFI Nforce4 Ultra motherboard (200Mhz FSB), GeForce 7900 GT with Nvidia drivers.

Isn't that good enough?  Do I really need something more powerful to play one file, or am I doing something wrong?  My friend plays them perfectly on his 1.83Ghz Mac Mini...

---

### Post by xzero1 on 2009-05-25
If you benchmark mplayer on this file (decoding only) you will probably find your cpu is not able to provide the required framerate. For HD video windows and other operating systems leverage specialized video card hardware to keep up. Nvidia has added support for this for some video cards in linux but 7xxx cards are not supported at least for now. 

See this post[ http://ubuntuforums.org/showthread.php?t=1165439&highlight=mplayer+benchmark]("http://ubuntuforums.org/showthread.php?t=1165439&highlight=mplayer+benchmark") to benchmark mplayer.

---

### Post by Mets on 2009-05-25
Thanks for the tip, I guess this explains a lot.  Do you know which other operating systems besides Windows leverage these capabilities?  I.e. any open source ones?

---

### Post by xzero1 on 2009-05-25
Well, its not really the operating system but the video card drivers. Linux is supported (vdapu driver) in at least some 8xxx and 9xxx cards with the latest drivers. I have a 7600Gt with pure video but there seems to be no vdapu support for the 7xxx series with Linux. Don't know if there ever will be.

---

### Post by xzero1 on 2009-05-26
I seem to have missed an option on the benchmark that might help a bit.
See this thread [http://ubuntuforums.org/showthread.php?t=934833](http://ubuntuforums.org/showthread.php?t=934833) in particular the 1st post.

---

### Post by binbash on 2009-05-26
you may also want to try CoreAVC + mplayer

---

### Post by xzero1 on 2009-05-26
> you may also want to try CoreAVC + mplayer     I wondered about that one too, but according to their website 720p/1080p @ 24-30fps requires a 2.2-2.8 Ghz cpu. My 2.2Ghz x2 plays 720p "acceptably" with mplayer. How much better is CoreAVC than mplayer with ffmpeg-mt? Now, though possibly acceptable play could result, this is *not* 720p or 1080p as their specs are 60fps! But has anyone tried it on linux? How does it perform?

---


---
title: "install ffmpeg in r19000-version not github..."
date: 2011-05-27
forum: Multimedia Software
---

### Post by adam42 on 2011-05-27
hi there 

I have installed ffmpeg via github on a ubuntu 11.04-machine.

An application - ClipBucket - require ffmpeg version r19000...

When doin a **ffmpeg -version** I get the following:


> ffmpeg version git-N-29993-ga4b6000, Copyright (c) 2000-2011 the FFmpeg developers
  built on May 26 2011 04:30:20 with gcc 4.5.2
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil    51.  2. 1 / 51.  2. 1
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  1. 0 / 53.  1. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  5. 0 /  2.  5. 0
  libswscale    0. 14. 0 /  0. 14. 0
  libpostproc  51.  2. 0 / 51.  2. 0
ffmpeg git-N-29993-ga4b6000
libavutil    51.  2. 1 / 51.  2. 1
libavcodec   53.  6. 0 / 53.  6. 0
libavformat  53.  1. 0 / 53.  1. 0
libavdevice  53.  0. 0 / 53.  0. 0
libavfilter   2.  5. 0 /  2.  5. 0
libswscale    0. 14. 0 /  0. 14. 0
libpostproc  51.  2. 0 / 51.  2. 0


How do I install ffmpeg version r19000 instead?

Cheers
Adam

---

### Post by ron999 on 2011-05-27
> **adam42 said:**
> 
An applæiocation - ClipBucket - require ffmpeg version r19000...


Hi
ClipBucket probably needs FFmpeg r19000 **or greater**.
So your version from github "built on May 26 2011" should be OK.

---

### Post by adam42 on 2011-05-27
You are right - 

> **ron999 said:**
> Hi
ClipBucket probably needs FFmpeg r19000 **or greater**.
So your version from github "built on May 26 2011" should be OK.

 - the problem is that according to the system check up it isn't good enough because it is not a r-version...

How can I 'trick' the system to make it a r-version?

Cheers
Adam

---

### Post by adam42 on 2011-06-14
No one can help me ? 

Cheers
Adam

---

### Post by FakeOutdoorsman on 2011-06-14
Tell the clipbucket author to update the FFmpeg check. Or you could try it yourself. Maybe lines 75 and/or 78 of *upload/cb_install/functions.php* are what you need to change (I didn't look at this in detail). Of course this won't address any changes to the FFmpeg commands since r19000.

FFmpeg development is very active and r19000 is ancient (May 2009). As of now there have been 11773 updates to FFmpeg since r19000.

---


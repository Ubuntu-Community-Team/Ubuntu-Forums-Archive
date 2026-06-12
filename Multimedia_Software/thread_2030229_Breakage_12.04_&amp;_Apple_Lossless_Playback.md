---
title: "Breakage: 12.04 &amp; Apple Lossless Playback"
date: 2012-07-20
forum: Multimedia Software
---

### Post by ytene on 2012-07-20
All, just had a weird experience with my 12.04 installation on my Shuttle X35 (32-bit). I went to launch Rhythmbox and put on some background music whilst I work, only to get an error message reporting something about a python component needing to download an additional package in order to be able to play an Apple Lossless file (ALAC Codec).

The weird thing is, this has been working perfectly since I built the machine from a 12.04 beta... I've never had a moment's trouble with accessing and playing back my iTunes library before. 

Now, I did notice on another of my machines that a recent update pulled in a lot of new python code. Does anyone happen to know if these fixes have broken anything sound-related? 

There was a hint in the error message that the problem might be resolved if I installed a package called alac-decoder. I've pulled that in and re-started Rhythmbox but it makes no difference. [Nothing in syslog either].

Thanks in Advance, 

C

Any suggestions would be very gratefully received...

---

### Post by mc4man on 2012-07-20
gstreamer decodes alac thru the 'gstreamer0.10-ffmpeg' plugin, maybe check if that is installed
(sounds like it was

If it is then you could try going in your home folder > .gstreamer-0.10 & deleting the registry.x86_64.bin or registry.i686.bin file
(view > Show Hidden Files if you don't see the .gstreamer-0.10 folder

---

### Post by ytene on 2012-08-19
Thank you, MC4MAN, that did the trick...

:grin:

---


---
title: "MKV Subtitles in Totem displaying \n"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by jchien on 2007-10-27
Basically I have some MKV files that I watch in Totem, but the subtitles shown display \n instead of new lines. Is there any way to fix this to correctly read the \n's as new lines?

---

### Post by rodwithz on 2007-11-14
Here is solution that worked for me under
ubuntu 7.10 gutsy.

1. Applications-> Add/Remove-> Sound & Video->
   Select Movie Player Totem (xine backend)
   for installation.

   This replaces totem-gstreamer with totem-xine.
   And I do mean replace.

2. System-> Administration-> Synaptic
   Package Manager
   Select libxine-ffmpeg, libxine-gnome and
   libxine-plugins for installation.

   This adds extra stuff.

3. Enjoy.  The bonus is that xine playback is much
   smoother than gstreamer.

---


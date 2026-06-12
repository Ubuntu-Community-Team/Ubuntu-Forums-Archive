---
title: "npviewer.bin blocks sound playback"
date: 2010-08-07
forum: Multimedia Software
---

### Post by movieman on 2010-08-07
Is there any way to get sound out of Ubuntu while npviewer.bin is running?

If I run Firefox and then try to use Rhythmbox or Vlc I get no sound, but the instant I kill npviewer.bin with Vlc running the sound from the video file starts playing; this is really getting to be annoying, particularly as I'm sure it's something that's been broken in the last year or so.

---

### Post by tgilber1 on 2010-09-01
You can fix this issue by removing nspluginwrapper and the 32-bit flash.  After removing the aforementioned files, install the 64-bit version of flash into your browser's plugin folder.  At this point, you should be able to play either flash and sound, or both with no problems.

---

### Post by lovinglinux on 2010-09-01
> **tgilber1 said:**
> You can fix this issue by removing nspluginwrapper and the 32-bit flash.  After removing the aforementioned files, install the 64-bit version of flash into your browser's plugin folder.  At this point, you should be able to play either flash and sound, or both with no problems.

The 64bit is no longer supported by Adobe and has critical vulnerabilities.

See [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

---


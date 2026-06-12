---
title: "XGL problems"
date: 2006-08-19
forum: Multimedia &amp; Video
---

### Post by nonex on 2006-08-19
cgwd: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
 compiz.real: GLX_EXT_texture_from_pixmap is missing
 compiz.real: Failed to manage screen: 0
 compiz.real: No managable screens found on display :0.0

---

### Post by TripleE on 2006-08-19
cgwd replaced gnome-window-decorator.  I am not sure what howto you used, but I used [http://www.ubuntuforums.org/showthread.php?t=225141](http://www.ubuntuforums.org/showthread.php?t=225141), and mine now works.  If you want to check out the problems I had, check out:
[http://www.ubuntuforums.org/showthread.php?t=236578](http://www.ubuntuforums.org/showthread.php?t=236578)

---

### Post by shiver on 2006-08-19
I though I might post here about my problems instead of making a new thread...

I can't get XGL to work, no matter what. I have a Radeon 9600 XT and fglrx 8.27.10 and direct rendering is working (if you can really say that, it's ATI after all). I'm using 32-bit Kubuntu with a custom 2.6.17 kernel, although using the standard kernel makes no difference. I have followed numerous howtos with different approaches, XGL as session or loading when kdm starts, on display 0 and 1 as well as shutting down kdm and running it from a terminal. None of these work. If I config it to use display 0, regular X starts. If I use display 1, direct rendering doesn't work and it starts up in software rendering and everything takes several seconds to respond if it doesn't crash the whole thing in the first place. Strangely, the switch user menu says I'm on :0 even when it's supposed to be in :1.

I welcome any ideas. I have tried Kororaa before and it worked.

---


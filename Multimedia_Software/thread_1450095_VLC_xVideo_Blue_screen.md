---
title: "VLC xVideo Blue screen"
date: 2010-04-08
forum: Multimedia Software
---

### Post by green0eggs on 2010-04-08
So I've been using VLC for ages and all of a sudden I get blue screen over my video output (solid blue like BSOD)... and the sound still works. I [read]("http://ubuntuforums.org/showthread.php?t=40273&highlight=blue+screen+video") that changing the output module fixed it.

The only output modules that work are 'OpenGL video output' and 'X11 video output'... OpenGL is really jerky and X11 has vertical lines through the frames.

So I reinstalled the package libxv1 which says its the xvideo whatnot

and now I've changed my blue screen of death to a black one... as in I still get audio but by video output is black rather than blue. 

Any thoughts? 

Odd that it's stopped working suddenly... I'm not even sure I've installed anything or run any updates.

---

### Post by no2498 on 2010-04-08
you have all the codes installed

sounds like a 264 error

open a terminal and type, smplayer
it tells you how to install it
and try the same videos

smplayer installs the 264 codes 

hope this helps

---

### Post by green0eggs on 2010-04-09
> **no2498 said:**
> 
smplayer installs the 264 codes 


Installing smplayer did the trick. xVideo now works. Thanks.

---

### Post by green0eggs on 2010-04-09
... ok I think I was a bit hasty. VLC now works with xVideo codec but when I click a DVD menu option it closes the movie window (but leaves controls so it's not crashing the whole thing).

I've tried playing DVD with no menus and I get 'Libdvd could not access block 512'.

I then ran VLC from terminal and tried the same thing (i.e. opening with no menus and I got this at the end of a list of messages...

```
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x002e2e84
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002e2e8a
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
libdvdread: Can't seek to block 483388
[00000388] dvdread demux error: read failed for block 512

```

---


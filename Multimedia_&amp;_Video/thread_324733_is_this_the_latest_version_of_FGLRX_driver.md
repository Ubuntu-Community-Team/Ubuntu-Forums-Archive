---
title: "is this the latest version of FGLRX driver?"
date: 2006-12-24
forum: Multimedia &amp; Video
---

### Post by endtransmission on 2006-12-24
ios ~ # fglrxinfo 
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY FireGL V5200 Pentium 4 (SSE2) (FireGL) (GNU_ICD)
OpenGL version string: 2.0.6011 (8.28.8)

ios ~ # 

Is this the latest version of the fglrx driver commonly available?  Every time I to to a VT (ctl alt f1) or hibernate or sleep, I come back with a completely black screen, with only a mouse pointer.  I have to ctl alt backspace to kill X and reinitiate.

Can anyone lend any assistance here?  I'm told the most recent version of the fglrx driver was to address this specific problem but the newest I see on the forums are 8.26 - which means I'm already ahead of the game and probably SOL.

I installed this using these instructions.
[http://www.ubuntuforums.org/showthread.php?t=291464&highlight=fglrx+howto](http://www.ubuntuforums.org/showthread.php?t=291464&highlight=fglrx+howto)

This is on an IBM z61p being driven by Edgy.

---

### Post by endtransmission on 2006-12-27
c'mon....bump

---

### Post by IanW on 2006-12-27
If you're up to installing it manually by following the stickied HOWTO above ([This one]("http://www.ubuntuforums.org/showthread.php?t=204910")),
you can go all the way up to version 8.32.5 which was released a couple of weeks ago.

From what I've read in that thread, the newest version seems to be very good for laptop support.

---


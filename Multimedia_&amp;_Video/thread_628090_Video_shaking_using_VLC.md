---
title: "Video shaking using VLC"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by alanpotpot on 2007-11-30
I recently did a clean install of Gutsy. When I watch videos it shakes. The audio is fine. But the video looks like it is stuttering. MPlayer works fine though. What could be the problem? Do I need to install other codecs?

---

### Post by vickiho on 2007-12-01
I'm having exactly the same problem. Worse, when I watch videos in Movie Player, the colors are inverted (although playback is not jerky like it is in VLC for me).

Can anyone help?

**EDIT: When I select X11 video output (preferences > video > output modules) as my output module, the jerkiness is gone. Hurrah!**

---

### Post by Romanovzky on 2008-02-05
Solved my problem to.

Thanks!

---

### Post by maximk on 2008-05-31
That's it. X11 output module solves the problem, but performance greatly decreases, because of software rendering.
Actually, the problem deals with 'Overlay' feature of video driver. I have ATI X200M (integrated video with shared memory) and with fglrx there is a shaking while playing video. If I swith to default 'radeon' driver, but still leave 'Overlay' turned on, then only volatile vertical color stripes is visible. Software redering (overlay off) is ok.

The main problem that CPU's overloaded while playing high quality (HDTV) mpeg4, resulting in frame lost and jerky movie. But CPU is capable of only decoding such stream, if output is delegated to video card.

I still have no solution, any help is appreciated :)

---


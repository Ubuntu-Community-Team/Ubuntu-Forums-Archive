---
title: "DVDs will play, but only on a quarter of the screen..."
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by russell-ault on 2007-08-02
Hi all,

This is my first post, so please bear with me if I look and sound like an idiot. :-)

I've been able to get DVDs to start playing on an older Sony Vaio (PCG-FX270) (the internal DVD player no longer works, so I'm using an external USB drive, also by Sony, if that matters). Sound comes out of the speakers, and video appears on the screen. Well, some of the screen anyway. For some reason, DVD video will only display on the left-hand quarter of the screen, reguardless of what program I'm using (I've tried Totem and VLC with identical results. And it doesn't matter if I'm in full-screen mode or windowed, but three-quarters of the screen where video should be appears black. As I say, though, the left-hand quarter displays the proper video (as in its not stretched, just oddly cropped-looking). I'm wondering if it's some kind of video overlay problem, but it seems to do that whether or not Video Overlay mode is on. Could this be some weird kind of X/hardware problem?

-Russ

---

### Post by russell-ault on 2007-08-05
bump (thanks in advance) :-)

---

### Post by scourge on 2007-08-05
It could be a hardware problem. What's the graphics chip in the laptop (Intel, NVIDIA, etc.)?
And which video output module are you using (XVideo, X11, OpenGL, etc.)? In VLC you can change the video output in the Preferences->Video->Output modules menu. If your graphics drivers work correctly then xv is usually the best option.

Oh, and could you post the contents of your /etc/X11/xorg.conf?

---


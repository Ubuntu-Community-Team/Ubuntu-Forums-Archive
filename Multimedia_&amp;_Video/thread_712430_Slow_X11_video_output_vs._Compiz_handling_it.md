---
title: "Slow X11 video output vs. Compiz handling it"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by rainwalker on 2008-03-01
I can set VLC to use the "Default" video output module, which I'm guessing would be Compiz handling it, and things will be fine except:

1. If I move the window, the video output doesn't move with it
2. The video won't show up in a screenshot (instead there's just blue where the video should be)
3. Fullscreen video will only work if opacity is set to 100%

As opposed to X11 output which does all of the above, except that it's slow. I can't play stuff fullscreen because the video becomes choppy, and even when it's not fullscreen my computer seems to have to work harder because the fan comes on sooner and more often (and more intensely).

It's really not a big deal, but it would be nice for the video to move with the window, not only when I just move it to another place on the screen but when I rotate my desktop cube and all that stuff as well.

Is there a way to fix this?

---

### Post by miciurin on 2008-03-03
Yep,

Kwin --replace before watching the video. Now you can have default video output in vlc.

---

### Post by rainwalker on 2008-03-03
> **miciurin said:**
> Yep,

Kwin --replace before watching the video. Now you can have default video output in vlc.

Erm...Is there a way to fix this without reverting to another WM?

---

### Post by Melcar on 2008-03-03
Only solution is to use X for rendering, and if that's not an option (bad performance for example) then either ditch Compiz or learn to live with flickering playback.  Another option would be to get an nvidia card and run their proprietary drivers, since people don't seem to complain about flickering video with them.

[https://wiki.ubuntu.com/RedirectedDirectRendering]("https://wiki.ubuntu.com/RedirectedDirectRendering")

---


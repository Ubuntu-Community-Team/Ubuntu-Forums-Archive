---
title: "VIdeo (HD) goes out of sync"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by SveinT on 2007-05-28
Hi,

I recently installed Ubuntu 7.04 and is enjoying it much so far, but when I try to play a HD video (720p) in mplayer the video quickly goes horribly out of sync with the audio. It plays fine in windows however. This does not happen with SD videos either. I thought it was due to CPU limitations, but my CPU isn't even adjusted to full load (1.6Ghz) when playing the video, it just runs at 1GHz per core. Even at this frequency setting neither of the cores reaches 100% - so CPU power certainly isn't the problem. I have compiz enabled and use SMPlayer frontend for mplayer. Any suggestions?

---

### Post by 3rdalbum on 2007-05-28
Try turning Compiz off - it's a program that your video would have to go through in order to play. If you're on an ATI card, also try logging out of XGL and into a normal session.

---

### Post by SveinT on 2007-05-28
> **3rdalbum said:**
> Try turning Compiz off - it's a program that your video would have to go through in order to play. If you're on an ATI card, also try logging out of XGL and into a normal session.

Thanks for your reply, unfortunately disabling compiz didn't do much. It still has sync problems.

---

### Post by pp7 on 2007-07-20
I am having EXACTLY the same problem.  Plays perfectly in windows but audio sync problems in Ubuntu.  Did anyone find a solution?

---

### Post by Gremlinzzz on 2007-07-20
Is your video driver set to X11 if not go to options preferences in smplayer and change it

---

### Post by SveinT on 2007-07-27
It's set to X11, yes. Still haven't found a fix to the problem...

---

### Post by rvm4000 on 2007-07-28
xv gives much better performance than x11. Try it.

For h.264 videos you can try this option: -lavdopts skiploopfilter=never

---


---
title: "specify which &quot;screen&quot; a program opens on?"
date: 2006-09-28
forum: Multimedia &amp; Video
---

### Post by evanc on 2006-09-28
So. I have an nVidea GeForce something card, and my xorg.conf is set up for two separate screens - a crt monitor and a tv (via s-video). This is working great. I can move the mouse between screens, but i can't drag windows across. No twinview. I can move the mouse over to the tv, browse to a video file, double-click, and it opens fullscreen in VLC and starts playing. Which is almost what I want....

I'd love to be able to stay on my CRT screen, browse to a video file, double-click, and have it open on the TV, fullscreen. Is there a way to specify (in a script, I'd imagine) which screen to open a program on? Then, could I associate that script with video files?

---

### Post by jkwarras on 2006-09-29
> **evanc said:**
> I'd love to be able to stay on my CRT screen, browse to a video file, double-click, and have it open on the TV, fullscreen. Is there a way to specify (in a script, I'd imagine) which screen to open a program on? Then, could I associate that script with video files?
I use the package nautilus-actions for that. You can then add an action associated to avi, mov, mpg, etc... to open videoplayer in fullscreen in the second display, via right-click on nautilus.

That's what I use as action:

totem --display=:0.1 --fullscreen

parameter: %M

BTW, anyone knows why the fullscreen playback is pixelated under ubuntu? (no matter what player I use, totem or mplayer). Under windows it's much better.

---


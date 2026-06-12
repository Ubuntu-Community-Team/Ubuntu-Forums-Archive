---
title: "Xine/Kaffeine Video Problems"
date: 2007-04-16
forum: Multimedia &amp; Video
---

### Post by iflanery on 2007-04-16
[FONT="Trebuchet MS"][SIZE="2"]Over the past couple days I've encountered a rather jarring problem with the video playback in both Xine and Kaffeine. Namely, the video output appears only in various shades of green and purple. Curiously, this problem is nonexistent in both gXine and Totem. The only problem I can see is that in the video settings for Xine there was no slider present in the Hue column. I promptly uninstalled Xine, thinking this would solve my problem; didn't. Now, I'm still having the same playback issues in Kaffeine, leaving me back at square one. Any possible ideas as to how I can solve this issue?[/SIZE][/FONT]

---

### Post by CRIKEY on 2007-04-30
ive had the same problems even on a fresh install did you figure it out (sorry about raising a dead topic)

---

### Post by andjui on 2007-05-20
i just had this problem - but look to have gotten rid of it

in the xine Engine Parameters -> video -> Beginner options
[INDENT]I set the drive to "opengl"[/INDENT]

xine Engine Parameters -> video -> Expert options
[INDENT]set opengl_renderer to "Image_Pipeline"[/INDENT]


No idea what the ideal settings are, but those work for me

---

### Post by OliW on 2008-01-12
Switching to opengl in xine worked for me but Kaffeine wasn't having any of it (kept saying it couldn't/wouldn't let me use opengl).

Not a biggy, as I prefer the minimalistic xine ui - thanks =)

---


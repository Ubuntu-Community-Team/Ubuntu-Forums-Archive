---
title: "gmplayer = error mplayer = no error"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by bpont on 2007-05-11
For some strange reason, when I invoke (as user) 'gmplayer' to play a video, I get the following error message:

```
[MGA] Couldn't open: /dev/mga_vid
Error opening/initializing the selected video_out (-vo) device.
```

However, when I invoke with 'mplayer' everything works fine.

Is this a bug?

---

### Post by oddsocks on 2007-05-12
I'm also having this problem!!! Help will be much appreciated

---

### Post by taurus on 2007-05-12
Edit ~/.mplayer/gui.conf

```
gedit ~/.mplayer/gui.conf
```
and change the driver for video_out from whatever it is right now to **xv**.  Save it and start gmplayer again.

```
gmplayer
```

---

### Post by catch007 on 2007-05-12
> **taurus said:**
> Edit ~/.mplayer/gui.conf

```
gedit ~/.mplayer/gui.conf
```
and change the driver for video_out from whatever it is right now to **xv**.  Save it and start gmplayer again.

```
gmplayer
```

I encountered the same problem. and what do you mean by "xv"?

---

### Post by taurus on 2007-05-12
Use xv driver for your video output.

---

### Post by zodmaner on 2007-05-12
Oh my god! It works!:biggrin: Thanks alot, Taurus! I also had this problem and now it is gone!

PS. What cause this problem? Is it because my card? (X700) or something else? And will we see it fix in the next version? Anyway, thanks for helping! :D

---

### Post by arkangel on 2007-05-12
just my 2 cents 

if your card is fully working ,   in gmplayer  with the secondary click there is a menu  (you can do it in the config file)  preferences and select  gl or gl2 

this will  improve the quality

---

### Post by Unix_Wizard on 2007-05-13
It's still buggy compared to mplayer. For example I was watching a movie on double size and after a few minutes it snapped back to original size for no reason.

---


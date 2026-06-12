---
title: "Mplayer"
date: 2007-05-12
forum: Multimedia &amp; Video
---

### Post by rokixz on 2007-05-12
I have installed Mplayer on UBUNTU, but it not works. It says that video out not available.
I've tryed on other distros(Archlinux, Slackware) and there's works.
Whats the problem ? ::confused:

---

### Post by taurus on 2007-05-12
Edit ~/.mplayer/gui.conf

Applications -> Accessories -> Terminal
```
gedit ~/.mplayer/gui.conf
```
and change the video_out from whatever it is to **xv**.  Save it and run it again from a terminal with

```
gmplayer
```

---


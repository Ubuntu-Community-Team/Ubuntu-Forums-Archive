---
title: "Playing DVDs using NVIDIA TV-out"
date: 2008-07-10
forum: Multimedia Software
---

### Post by fuffzig on 2008-07-10
Hallo all,

I have a problem when playing DVDs in mythbuntu 8.04. I have a TV connected to an NVIDIA graphics card using the proprietary driver.
When playing DVDs i recognize a horizontal offset in the picture at 30% from top of the screen. This happens during fast moving scenes.
I have enabled "SyncToVBlank" in the graphical nvidia-settings dialog (XVideo Settings and OpenGL settings). How do I enable and verify that in a terminal? Where are these settings made?
I also added this to my device section in xorg.conf:

```
Option          "UseEvents"     "True"
```

Thanks

---

### Post by Prefix100 on 2008-07-10
Just out of interest.

I have a cable on my nVidia card that I have no idea what its for,
is this what you used to connect your TV?

[ATTACH]77140[/ATTACH]

---

### Post by fuffzig on 2008-07-10
> **Prefix100 said:**
> Just out of interest.

I have a cable on my nVidia card that I have no idea what its for,
is this what you used to connect your TV?

[ATTACH]77140[/ATTACH]

Could be. I simply have an SVIDEO out on my card and bought a cable on my own.

---

### Post by xc3RnbFO8P on 2008-07-10
> **Prefix100 said:**
> Just out of interest.

I have a cable on my nVidia card that I have no idea what its for,
is this what you used to connect your TV?

[ATTACH]77140[/ATTACH]

Its a Component Video:
[http://en.wikipedia.org/wiki/Component_video]("http://en.wikipedia.org/wiki/Component_video")
Here is S-video:
[http://en.wikipedia.org/wiki/S-Video]("http://en.wikipedia.org/wiki/S-Video")

---

### Post by fuffzig on 2008-07-10
The problem occurs when I use Mythbuntus internal player, mlayer or xine with xvideo output. When using mplayer with gl output, everything's fine.

---

### Post by cariboo on 2008-07-10
The three rca plugs are for composite output/input these are basically the lowres input/output used on vcr's and really inexpensive dvd players.

Jim

---


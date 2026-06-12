---
title: "Only sounds through HDMI in certain modes"
date: 2014-07-21
forum: Multimedia Software
---

### Post by snufk1n on 2014-07-21
I'm running Ubuntu Server 14.04 LTS with a GUI installed. The sever is connected to my TV through a receiver.

The problem I'm having is that only certain modes result in sound being heard. For instance
```
$ xrandr --output HDMI2 --mode 1920x1080 --rate 60.0
``` (this is the prefered mode according to xrandr) results in a fully functioning video, but no sound.

```
$ xrandr --output HDMI2 --mode 1920x1080i --rate 50.0
``` results in both sound and video, but I'd much rather use the preferred mode and refresh rate due to image quality.

How do I solve this?

---

### Post by sp40140 on 2014-07-21
This might be due to drivers. What vid card are you running and what drivers do you have installed?

---


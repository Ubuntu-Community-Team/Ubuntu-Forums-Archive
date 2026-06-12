---
title: "How to use &quot;Separate X Server&quot; setting in nvidia-settings?"
date: 2010-09-16
forum: Multimedia Software
---

### Post by applegrew on 2010-09-16
In nvidia-settings I see, alongwith Disabled and TwinView settings, "Separate X Server". I tried choosing the option for my LCD (connected via HDMI), but I get a blank screen, presumably since the LCD's X server has nothing to render.

How do I direct any application (say vlc) to use that X Server instead of the Monitor's X server? :D

---

### Post by guerillero on 2011-01-22
I believe it can be done through
```
DISPLAY=":1.0" mplayer blabkabla.avi
```

---


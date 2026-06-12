---
title: "global overscan setting for nvidia proprietary driver?"
date: 2010-05-23
forum: Multimedia Software
---

### Post by jejones3141 on 2010-05-23
I have a system that I'm connecting to my LG HDTV. I got a PNY nvidia GT 220 based card, which I bought because it would perform adequately and because it supports HDMI; I wanted to just use one cable.

Lucid Lynx installed fine. The image suffered from overscan, but I installed the proprietary nVidia driver--nvidia-settings gives one control over overscan. I adjusted it suitably... but it seems to only affect the screen when I am logged in. The GDM screen still suffers from overscan, so I can't use the controls at the bottom to choose KDE rather than GNOME, etc. When my wife logs on, she has to adjust overscan for her.

Is there a way to set the overscan control once and for all, so it comes out right in all circumstances?

---

### Post by wojox on 2010-05-24
Are you adjusting it from root?

```
gksudo nvidia-settings
```

---

### Post by jejones3141 on 2010-05-28
> **wojox said:**
> Are you adjusting it from root?

```
gksudo nvidia-settings
```

I had typed "sudo nvidia-settings" from a terminal, but you're right, gksudo is the way to sudo GUI-oriented programs, so I did that. The GDM screen is unchanged, with just a strip of the panel at the bottom that should let me choose my session etc. visible above the edge of the monitor.

---


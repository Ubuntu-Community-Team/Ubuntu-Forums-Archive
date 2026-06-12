---
title: "adding modeline permanent"
date: 2014-05-15
forum: Multimedia Software
---

### Post by LonelyStar on 2014-05-15
Hey,

I have a macbook pro retina and I want to use the screen with have its full resolution (because otherwise objects get very different in size on the external monitor).
So that would be "1280x800". Unfortantly that mode does not appear in the resolution settings.

But I can add it with xrandr:

```

xrandr --newmode "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
xrandr --addmode eDP1 1280x800_60.00

```

Now I want these to be added permanently to, so that they are remembered after restart.
Yet, I do not have xorg.conf, and everything works well without it.

Can I somehow add the modeline to xorg.conf, without having to have a full blown xorg.conf???

Thanks!
Nathan

---


---
title: "xrandr -q flicker frenzy"
date: 2009-01-14
forum: Multimedia Software
---

### Post by frediE on 2009-01-14
i have a laptop with an intel 915 video card.  there is flickering every time i start a gtk application.  it can be reproduced every time by running the following command.
```
xrandr -q
```


i can't seem to find a fix for ubuntu 8.10 gnome.  there seems to be a good fix for kde by disabling a service named "Detecting RANDR (monitor) changes".

any masterful insight would be great.  thanks!

---

### Post by krei on 2009-03-03
Hi there,

Afraid I can't offer 'masterful insight', but I do have similar problems with the same graphics card when xrandr is invoked. Interestingly in my case, this only affects an external monitor (LVDS display remains stable), and only started happening after upgrading my xserver and xrandr packages (old xorg-i810 and xrandr 1.1 showed no such problems). So, one option may be to downgrade (I found the earlier packages perfectly usable on my hardware), but surely there's a better answer?

Cheers,
Alex.

---


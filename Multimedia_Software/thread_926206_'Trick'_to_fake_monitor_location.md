---
title: "'Trick' to fake monitor location"
date: 2008-09-21
forum: Multimedia Software
---

### Post by Macuyiko on 2008-09-21
I'm currently using the Xorg-intel video driver which does not support DRI rendering if you use a Virtual screen larger then 2048x2048 (they're working on it for Interprid though).

With my old 4:3 monitor I used to do this:

xrandr --output LVDS --mode 1024x768 --output VGA --left-of LVDS --mode 1024x768

Which was a pity because I couldn't use a 1600x1200 resolution, but it was doable.

I'm currently using xrandr to connect my widescreen monitor as such:

xrandr --output LVDS --mode 1024x768 --output VGA --above LVDS --mode 1920x1200

But this puts the monitors above each other, which is a bit annoying and counter-intuitive. Is there a way to manipulate this so I can still drag windows and move my mouse from left to right? Maybe with wmctrl? So that in the Virtual screen the viewports are below eacht other, but the interface (gnome) behaves as if they're next to each other.

Thanks!

---


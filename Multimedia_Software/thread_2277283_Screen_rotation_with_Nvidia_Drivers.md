---
title: "Screen rotation with Nvidia Drivers"
date: 2015-05-07
forum: Multimedia Software
---

### Post by sephy7killermech2 on 2015-05-07
I have been scouring google for two days trying to fix my screen rotation problem. I can rotate my screen no problem with the Nouveau drivers, but those drivers pretty much make my games unplayable, which is not acceptable to me. With the Nvidia 331.113 drivers my games perform well but I cannot rotate my screen. I tried editing my xorg.conf file by placing "RandRRotation" "on" under both device and screen, I did each of these tests separately, but had no success with the command line. I tried both xrandr --output LVDS1 --rotate inverted and I tried xrandr -o inverted. with the former I get this.

xrandr: output LVDS1 cannot use rotation "inverted" reflection "none"

And with the latter the screen flashes but no change is made. 

I would love to continue using Ubuntu but this might be a deal breaker for me. I need to mount my laptop upside down at work and since I'm there for weeks at a time I need to be able to relax with my games as well. I can't tell you all how much I'd appreciate some help on this matter. Thank you for your time.



<Edit> I meant to place this in hardware. If this could be deleted that would be great, I'll just go ahead and post this in the correct forum. Sorry for the trouble.

---


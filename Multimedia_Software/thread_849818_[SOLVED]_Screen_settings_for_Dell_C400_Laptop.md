---
title: "[SOLVED] Screen settings for Dell C400 Laptop"
date: 2008-07-04
forum: Multimedia Software
---

### Post by EdLinq on 2008-07-04
Everything was fine using 1024 X 768 resolution until I tried to connect an external display to the laptop.  That is when I lost the settings for the laptop screen.  Now I only have 640 X 480.  I know I have an i830 graphics card with the i810 intel Integrated Graphics Chipset.  What I do not know is what screen model I (had) need to choose.  So far none of the ones I would have thought have worked.  Might someone have a similar unit and could send me the settings?

---

### Post by overdrank on 2008-07-04
> **EdLinq said:**
> Everything was fine using 1024 X 768 resolution until I tried to connect an external display to the laptop.  That is when I lost the settings for the laptop screen.  Now I only have 640 X 480.  I know I have an i830 graphics card with the i810 intel Integrated Graphics Chipset.  What I do not know is what screen model I (had) need to choose.  So far none of the ones I would have thought have worked.  Might someone have a similar unit and could send me the settings?

HI and have you tried to reconfigure your xorg with the command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Or boot into recovery mode and use the xfix option.

---

### Post by EdLinq on 2008-07-05
Wow,  Thank you very much.  That was interesting.  The system created a custom profile for the video card and the screen.  It is not what I had, but it works great.  I'm back in busisness.

---

### Post by overdrank on 2008-07-05
> **EdLinq said:**
> Wow,  Thank you very much.  That was interesting.  The system created a custom profile for the video card and the screen.  It is not what I had, but it works great.  I'm back in busisness.

Great and good luck! :popcorn:

---


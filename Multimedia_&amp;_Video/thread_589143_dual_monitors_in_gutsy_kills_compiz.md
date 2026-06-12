---
title: "dual monitors in gutsy kills compiz"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by oldmanstan on 2007-10-23
i have dual 22 inch widescreen lcds running on an nvidia 6800 256mb card. with a single monitor compiz works fine (the default settings in gutsy). but the only settings under which i can get the dual displays going (selecting them both as 1680x1050 lcds in the screens and graphics dialog) seems to kill compiz, when i log back into gnome the visual effects is set to none. if i try to turn the effects back on i get "desktop effects could not be enabled" and they stay off.

is this a problem with ubuntu/compiz/drivers? or is this just how it tells me i've pushed my video card beyond what it can do?

if it is the latter case: would adding a second video card help? can compiz run through 2 cards at once?

thanks!

---

### Post by molo on 2007-10-23
I don't know if this is the case with your nVidia card, but my ATI card supports a maximum texture resolution of only 2048x2048.  This means that I can't run 3D effects with  a bigger desktop, such as my dual screen 2560x1024 resolution.  If I lower the resolution to 2048x768, 3D effects work fine.   So try lowering your resolution and see if both screens work.

---

### Post by hfw on 2007-10-24
I am having the same problem you are having.  Hopefully I can find an answer somewhere tonight.  i think your card can handle it. I have a 128mb fx5500, and it was running the dual screens in compiz-fusion fine with feisty.

---


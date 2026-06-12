---
title: "[SOLVED] Desktop Effects with Samsung 226BW and 1680x1050 resolution"
date: 2007-08-09
forum: Multimedia &amp; Video
---

### Post by JawsThemeSwimming428 on 2007-08-09
I just bought a Samsung 226BW 22" LCD monitor and I could not get it working through DVI. So I plugged in VGA and it worked. I changed the resolution to 1680x1050 with the Screen Resolution tool and it worked, but It won't allow desktop effects. If I turn desktop effects on there is no title bar (no x, maximize, and minimize buttons on the top of the window) and when I try to load Terminal, it just brings up a blank white box, no borders and no text and no cursor. I then open Konsole and it works but there is no title bar! How do I fix this and use desktop effects?

---

### Post by sullivan.t on 2007-08-10
I am having this issue as well.  And I didn't even install beryl - I futzed with my nvidia config and with desktop effects on, this happened/happens.   I tried beryl just for kicks - I think it looks cool, but I still am missing the title bar as well.

---

### Post by JawsThemeSwimming428 on 2007-08-12
I haven't found a fix yet. I have been tinkering with the settings for the card but nothing seems to work. Anyone have anything that might help?

---

### Post by Alexander2007 on 2007-08-12
Open a terminal window and type: ```
sudo nvidia-xconfig --allow-glx-with-composite --add-argb-glx-visuals --disable-glx-root-clipping
```

---

### Post by JawsThemeSwimming428 on 2007-08-13
Thanks, but that didn't work. The title bars and borders are still gone from all of the windows when I enable desktop effects.

---

### Post by Rhubarb on 2007-08-13
You need emerald-themes
```
sudo aptitude install emerald-themes
```

I've got the same monitor here (Samsung SyncMaster 225BW), after installing emerald-themes, Desktop effects (and compiz-fusion / beryl) should work fine for you.

---


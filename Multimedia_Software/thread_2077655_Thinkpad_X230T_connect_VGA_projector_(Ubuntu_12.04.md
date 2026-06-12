---
title: "Thinkpad X230T: connect VGA projector (Ubuntu 12.04)"
date: 2012-10-29
forum: Multimedia Software
---

### Post by maxchen on 2012-10-29
Hope this may help.
the native screen is 1366x768, however, most projector is 1024x768. If I mirror the screens, will be 1024x768, and the Pen stylus will not point correctly. Thus

[HTML]xrandr --output VGA1 --scale 1.334x1 --same-as  LVDS1 --auto[/HTML]will rescale the 16:9 of touch screen (1366x768 ) to 4:3 VGA (1024x768 ), and the pen stylus and finger touch works properly.

---


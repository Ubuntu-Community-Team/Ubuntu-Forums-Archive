---
title: "fuxxored my resolution, can't see to change it back"
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by Evil Wayz on 2008-01-04
I changed the resolution on my screen from 600x800 to 1024x1280.  Now everything is smeared, but it runs fine.  I need to know the commands in terminal to change it back, because the computer doesn't realize the screen is not readable and didn't automatically fo to low graphics mode.

---

### Post by solar george on 2008-01-04
Try,
```
xrandr -s 800x600
```
Then use the resolution settings to set it permanently back.

---


---
title: "nVidia settings not saving: Alternate Fix"
date: 2007-10-12
forum: Multimedia &amp; Video
---

### Post by torsoboy on 2007-10-12
Seems like a lot of people have this problem, and I've found multiple 'solutions' for it (many of which my n00b-ness prevents me from comprehending),  But this seems  like the easiest way to go about saving your settings:

ALWAYS BACKUP YOUR XORG.CONF BEFORE MUCKING AROUND WITH IT.

Open nvidia-settings, make your changes and instead of saving as xorg.conf save as xorg.conf_1 or something similar

go back to the terminal and type

cd /etc/X11

sudo rm  xorg.conf

sudo mv  xorg.conf_1 xorg.conf

... and you're done. so easy, it feels like you're cheating.

---

### Post by K.Mandla on 2007-10-24
Moved to Multimedia & Video.

---


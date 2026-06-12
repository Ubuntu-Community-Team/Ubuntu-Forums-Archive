---
title: "How to disable scaling with Nvidia?"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by TS28 on 2007-06-03
Hello, I have been having trouble finding how I disable resolution scaling with Nvidia.

I have a dell 2007, and in windows I am able to set the Nvidia panel to "do not scale" which if a resolution is smaller than my native (1680x1050) it would simply form black boxes around the application, in this case, Warcraft 3.

Help appreciated as always :)

-Stefan

---

### Post by reclusivemonkey on 2007-06-03
Try

```

sudo nvidia-settings

```

The options under GPU0 should have a scale setting. Although whether or not it will work is another matter. Make sure you backup xorg.conf first as always when playing with nvidia-settings! ;-)

---


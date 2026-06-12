---
title: "NVidia Compiz GLX_EXT_texture_from_pixmap"
date: 2006-05-30
forum: Multimedia &amp; Video
---

### Post by npodges on 2006-05-30
I've been having problems getting compiz to work (i had it working a few months ago just fine.)

after looking around a lot, i found a lot of people in the 100+ page thread have the same problem, and cant figure it out.

none of the how-to's seem to be updated for this, but here it is:
[QUOTE=sciyoshi]Hey subsonic and anyone else with GLX_EXT_texture_from_pixmap problems:

The new nvidia packages have files in different locations. Here's the command I used to get things working:
```

sudo ln -sf /usr/lib/nvidia/libGL.so.1.2.xlibmesa /usr/lib/libGL.so.1
```[/QUOTE]

anyone who has been getting that error (you know which one, if it's you), that command works like a charm.
thanks sciyoshi

---

### Post by hanzomon4 on 2006-08-30
This command crashes X on my setup

---


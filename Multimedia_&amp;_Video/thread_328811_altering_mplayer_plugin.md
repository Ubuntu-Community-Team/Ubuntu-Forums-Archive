---
title: "altering mplayer plugin"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by Mateo on 2006-12-31
Is it possible to alter the mplayer plugin?  one problem with it is that it doesn't use the -zoom option while in fullscreen.  if it were possible to add that to the command for the plugin, it would be nearly perfect.

---

### Post by taurus on 2006-12-31
Applications -> Accessories -> Terminal
```
nano ~/.mplayer/config
```
and add
```
zoom=yes
```
to it!!!

---


---
title: "better 3D performance WITHOUT ati drivers"
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by jamesford on 2006-06-01
this is sort of making me wonder. i did a clean dapper install and played around with the screensavers before i isntalled the ati fxgrlr drivers ,and they all worked fine, even the 3D ones. after i installed the fxgrl things most of the screensavers are really jerky and some hardly run at all.
fgl_glxgears runs fine tho with ati drivers installed

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)

any idea why?

---

### Post by towsonu2003 on 2006-06-02
if you are installing the drivers from ati's website, I believe you should remove linux-restricted-modules. you might wanna search the forum for a howto on that...

yes, checking out a howto for ati would be a good idea. 

another possibility is: ati has an extremely bad driver writer team as far as I see w. my hardware performance...

---


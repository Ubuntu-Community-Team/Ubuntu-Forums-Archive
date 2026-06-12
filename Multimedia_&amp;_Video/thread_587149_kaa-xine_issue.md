---
title: "kaa-xine issue"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by johndela1 on 2007-10-22
I'm using kaa 0.1 and I am getting errors

For example,

from a python shell:

Type "help", "copyright", "credits" or "license" for more information.
>>> from kaa.xine import Version
>>> VERSION
*** glibc detected *** python: free(): invalid pointer: 0x08374960 ***


anyone see this and if so, have a fix or any ideas?

---

### Post by johndela1 on 2007-10-24
The issue seems to be in the OPENGL_VSYNC code in the display module.
 I've configured this out of the build for now since we probably won't use
 it anyway. 

After disabling this, things work.

---


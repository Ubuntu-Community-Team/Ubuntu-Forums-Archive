---
title: "totem: how to use x11-video ?"
date: 2010-05-24
forum: Multimedia Software
---

### Post by kirol on 2010-05-24
On my laptop (gt220m, nvidia-195 driver), I have to use either X11 or OpenGL video instead of the default back-end to be able to see videos played with VLC. How can I do the equivalent for totem (whose default video output show nothing either)

---

### Post by xzero1 on 2010-05-24
Try the command "gstreamer-properties".

---

### Post by kirol on 2010-05-24
Thanks xzero1, choosing "No Xv" as video output works.

Perhaps the xv extension can be enabled in xorg.conf for nvidia?

---


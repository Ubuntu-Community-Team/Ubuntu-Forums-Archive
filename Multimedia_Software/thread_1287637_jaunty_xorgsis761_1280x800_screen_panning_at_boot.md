---
title: "jaunty xorg/sis761 1280x800 screen panning at boot"
date: 2009-10-10
forum: Multimedia Software
---

### Post by barb3tta on 2009-10-10
EDIT: the problem was solved just after a deep check at the Xorg.0.log file.
It seems that when I specify a modeline in my xorg.conf and use it in "Modes" section, it was not recognized and not used by xorg.
I simply used a default mode and everything goes fine... lucky me!

---


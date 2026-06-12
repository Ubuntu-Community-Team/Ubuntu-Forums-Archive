---
title: "I Broke X and DRI"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by rmx.dave on 2007-10-18
I was trying to fix Gutsy's horribly slow frame rates by enabling Direct Rendering. I did some googling and saw someone suggest changing the permissions of /dev/dri to 666. I did that...and now X can't detect my monitor. I'm stuck at 640x480 resolution and really slow refresh rates. Also, I look back in /dev to check it out - and the dri folder is gone!

Help! How can I undo this foolish mistake?

---

### Post by rmx.dave on 2007-10-18
Well I reinstalled X, uninstalled XGL, and crossed my fingers. Everything seems to work now!

---


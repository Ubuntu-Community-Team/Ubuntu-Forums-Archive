---
title: "fglrx prevents X from starting"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by SteinbergerNate on 2006-06-14
After a recent upgrade, I could no longer get OpenGL to work. I started poking around and found in my xorg.conf that it had "ati" as the driver instead of "fglrx" I tried replacing this line with fglrx and rebooted. X never started but the computer still responded to restart commands like ctrl-alt-del. I got back into the recovery mode and changed the line back to ati and everything worked fine except that I still had no OpenGL. Does anyone have any solutions?

---

### Post by SteinbergerNate on 2006-06-14
Ok. I figured it out. I edited the xorg.conf one more time to point to the fglrx driver and then downloaded an older version of libgl.so.1.2. It works like a charm now.

---


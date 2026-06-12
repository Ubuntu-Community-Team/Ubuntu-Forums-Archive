---
title: "How Do I Swap Xorg.conf Files Dynamically?"
date: 2008-07-23
forum: Multimedia Software
---

### Post by SuperMike on 2008-07-23
When my laptop is connected to a flat panel display, I have an xorg.conf file that I created (it took me like 10 hours to build and get working right, unfortunately) that is optimal for that environment. But when I'm on the road, I have a completely different xorg.conf file that is optimal for that environement. In laptop-only mode, I also turn on 3D effects.

So I have that working, but I don't know a way yet to detect the separate monitor on boot and use the appropriate xorg.conf file. I tried creating a startup script that uses ddcprobe, but unfortunately it's always reporting an attached monitor even when it's not attached.

---


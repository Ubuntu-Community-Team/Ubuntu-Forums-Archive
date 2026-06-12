---
title: "Direct Rendering"
date: 2008-05-06
forum: Multimedia Software
---

### Post by apche93 on 2008-05-06
Hi, I recently upgraded to ubuntu 8.04 and before my direct rendering worked fine, whereas now, it doesnt seem to be working.  Does anyone have an idea?

```
$ glxinfo |grep direct

libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

I did that before the upgrade and it said that i did have direct rendering.  Did the upgrade break something?

---

### Post by Melcar on 2008-05-07
You will have to re-install your video drivers.

---


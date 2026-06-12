---
title: "glx full screen flickers, dispatch error"
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by Phantom784 on 2007-11-21
Whenever I try to use either a screen saver or a full screen game, the screen flickers really badly, and fonts in the game (urban terror) don't display correctly.  However, direct rendering is enabled (on an ati rage 128 ).  In glxinfo, i'm getting these three errors, which I think might have something to do with the problem
```
DISPATCH ERROR! _glapi_add_dispatch failed to add glAreTexturesResident!
DISPATCH ERROR! _glapi_add_dispatch failed to add glGenTextures!
DISPATCH ERROR! _glapi_add_dispatch failed to add glIsTexture!
libGL warning: 3D driver claims to not support visual 0x4b
```

then, in /var/log/Xorg.0.log, I see ```
(WW) AIGLX: 3D driver claims to not support visual 0x23
``` repeated for hex values 0x23 to 0x32

finally, when I run urban terror, the console repeats the error ```
Mesa 7.0.1 implementation error: User called no-op dispatch function (an unsupported extension function?)
Please report at bugzilla.freedesktop.org
```

any ideas?

---

### Post by Phantom784 on 2007-11-24
anyone?

---

### Post by cool2000m on 2008-06-27
bump! I have the exact same problems. anyone know an answer to this?

---


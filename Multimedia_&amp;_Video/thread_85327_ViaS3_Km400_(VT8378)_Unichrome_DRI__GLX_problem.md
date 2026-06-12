---
title: "Via/S3 Km400 (VT8378) Unichrome DRI / GLX problem"
date: 2005-11-02
forum: Multimedia &amp; Video
---

### Post by lxevolution on 2005-11-02
Hello.
Did anyone manage to enable direct rendering on VT8378 Unichrome IGP? When I install DRI support from the DRI website and restart X is tells me that "version mismatch". I copy the via_drv.o file (i forgot where i found it) and it works like a charm. now glxinfo tells me that drmOpen is unrecognized command. I copy the libGl.so.1.2 (once again i forgot the source) and glxinfo tells me that dri is disabled. also my xorg log says

(EE) via(0): [dri] VIADRIScreenInit failed because of a version mismatch.
[dri] libDRI version is 5.0.0 but version 4.0.x is needed.
[dri] Disabling DRI.

can anyone help me?

---


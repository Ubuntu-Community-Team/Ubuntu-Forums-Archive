---
title: "nvida GLcore problem"
date: 2006-07-25
forum: Multimedia &amp; Video
---

### Post by rj45 on 2006-07-25
Hi folks - 

running Dapper 2.6.15-23-amd64-generic with a NV GeForce 6600.
Installed 8762 drivers from NVidia web site about a month ago.

Everything has been running great, but my system locked up
today, and now can't seem to find libGLcore.  Xorg.log says:
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: _nv000012gl
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(II) UnloadModule: "GLcore"
(II) UnloadModule: "glx"
(II) Unloading /usr/lib/xorg/modules/extensions/libglx.so
(EE) Failed to load module "glx" (a required submodule could not be loaded, 7)

I've already tried re-install the 8762 drivers, with no change.
Can anyone tell me where the GLcore libs live?

TIA,
-Don:-?

---

### Post by LordRaiden on 2006-07-25
nvidia does not use GLCore. remove the line Load glcore from your xorg.conf file.

---

### Post by rj45 on 2006-07-25
> **LordRaiden said:**
> nvidia does not use GLCore. remove the line Load glcore from your xorg.conf file.

Gracias, mi amigo, for your quick and friendly answer.

I found the problem- somehow the "nv" driver lib "libglx.so" had been 
installed instead of the 8762 drivers "libglx.so.1.0.8762 and
then sylinked to the .so file.

Removed the offending file from /usr/lib/xorg/modules/extensions and
symlinked the 8762 one, and life is good once more.  
Back to fraggin!

regards,
-Don:)

---


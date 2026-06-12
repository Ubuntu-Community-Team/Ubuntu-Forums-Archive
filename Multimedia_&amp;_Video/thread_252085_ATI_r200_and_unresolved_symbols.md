---
title: "ATI r200 and unresolved symbols"
date: 2006-09-06
forum: Multimedia &amp; Video
---

### Post by fasaxc on 2006-09-06
Hi,

My 3D set-up seems to be a complete mess, I tried the DRI driver which worked (out of the box if I remember) then switched to fglrx which was too unstable. Finally I switched back but now I get no 3D. I have removed all fglrx packages and modified my xorg.conf accordingly. Xorg.0.log reports Direct rendering enabled but I get "libGL error: dlopen /usr/lib/dri/r200_dri.so failed (/usr/lib/dri/r200_dri.so: undefined symbol: _glapi_get_dispatch)" when I run glxinfo with LIBGL_DEBUG=verbose. 

The latest thing I tried was explicitly copying the contents of the xorg dri package to the file system, and this worked -- I had 3D all of yesterday but apparently an auto-update has broken it again.

Does anyone know of a method to completely remove a set of packages (preferably without removing their dependencies), deleting all their files and reinstalling from a clean slate. I get the impression that apt is not overwriting files that are shared between different modules or that my efforts have had this effect.

Any ideas?

-Shaun

---

### Post by fasaxc on 2006-09-07
Solved: The /usr/lib/libGL.so.1 symlink was pointing to the wrong file. It was pointing to /usr/lib/libGL.so.1.2.bak instead of /usr/lib/libGL.so.1.2.

Incidently, this wasn't the end to my problems, every time ldconfig (see man ldconfig) runs it would put the symlink back to the wrong file. I guess it must check the dates on any file starting libGL.so.1 and symlink the most recent. Deleting the .bak file seems to have solved the problem.

---


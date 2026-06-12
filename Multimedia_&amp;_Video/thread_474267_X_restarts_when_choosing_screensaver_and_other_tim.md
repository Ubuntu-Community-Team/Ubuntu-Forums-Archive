---
title: "X restarts when choosing screensaver and other times"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by mscdex on 2007-06-14
I'm running Xubuntu (to be specific) on a machine with a 3Dfx Voodoo3 Banshee. I noticed that when I go to manage my screensaver settings, it restarts X if I select certain screensavers (I'm guessing ones that are 3d or accelerated ones?). Here is the contents of the last lines of the Xorg log from /var/log:

```
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
DRIUnlock called when not locked

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]
2: /usr/lib/xorg/modules/extensions//libglx.so [0xb7ba152a]
3: /usr/lib/xorg/modules/extensions//libglx.so(DoMakeCurrent+0x2d1) [0xb7b6a661]
4: /usr/lib/xorg/modules/extensions//libglx.so [0xb7b6a8f9]
5: /usr/lib/xorg/modules/extensions//libglx.so [0xb7b6cacc]
6: /usr/bin/X [0x81424ce]
7: /usr/bin/X(Dispatch+0x19f) [0x808c61f]
8: /usr/bin/X(main+0x495) [0x8074785]
9: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7cfeebc]
10: /usr/bin/X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal server error:
Caught signal 11.  Server aborting

(II) AIGLX: Suspending AIGLX clients for VT switch
```

---

### Post by MichiganMan on 2007-06-17
Do you have a 3DFX Voodoo card?  I just ran into this problem with Xubuntu, too.  

Searching for 3DFX Voodoo in Synaptic will produce, among others, files that need to be installed to make use of the Voodoo's 3D capabilities.  glide2-bin, and libglide3 I believe are the ones that solved my problem.

---


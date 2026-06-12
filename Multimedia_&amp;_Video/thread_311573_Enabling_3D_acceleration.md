---
title: "Enabling 3D acceleration"
date: 2006-12-03
forum: Multimedia &amp; Video
---

### Post by trowa_zero on 2006-12-03
I want to enable my 3D acceleration.  I have a VIA V8M800 Unichrome IGP and when I run glxinfo it says direct rendering no.

I have Ubuntu Edgy Eft and AMD64.

From this trouble shooting guide ([http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=3DTroubleShooting](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=3DTroubleShooting))

Originally is said that unichrome_dri.so was missing so I followed these directions as best I could to build it  ([http://dri.freedesktop.org/wiki/Building)](http://dri.freedesktop.org/wiki/Building)).

and now it says 

libGL: XF86DRIGetClientDriverName: 5.0.0 unichrome (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/unichrome_dri.so
libGL error: dlopen /usr/lib/dri/unichrome_dri.so failed (/usr/lib/dri/unichrome_dri.so: undefined symbol: drmCloseOnce)
libGL error: unable to load driver: unichrome_dri.so

What do I need to do to get it to work?  Or what information does someone need to help me?

---

### Post by flywheelbot on 2007-11-06
Do you have the package libgl1-mesa-dri installed?

According to packages.ubuntu.com, the file you need (usr/lib/dri/unichrome_dri.so) is there.  Might try that--I just had a similar experience.  Might be different for the AMD64, though.

---

### Post by albertlash on 2008-01-27
Got the same problem... installing libgl-mesa-dri now.

---


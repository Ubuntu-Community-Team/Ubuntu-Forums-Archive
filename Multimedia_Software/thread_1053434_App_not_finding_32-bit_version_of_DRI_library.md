---
title: "App not finding 32-bit version of DRI library"
date: 2009-01-28
forum: Multimedia Software
---

### Post by niten on 2009-01-28
I'm trying to use a 32-bit app that uses OpenGL, and it's failing on me.  Here's the error that debug gives me:

> libGL: XF86DRIGetClientDriverName: 1.9.0 i915 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/tls/i915_dri.so
libGL: OpenDriver: trying /usr/lib/dri/i915_dri.so
libGL error: dlopen /usr/lib/dri/i915_dri.so failed (/usr/lib/dri/i915_dri.so: wrong ELF class: ELFCLASS64)
libGL error: unable to load driver: i915_dri.so
libGL: OpenDriver: trying /usr/lib/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/dri/swrast_dri.so
libGL error: dlopen /usr/lib/dri/swrast_dri.so failed (/usr/lib/dri/swrast_dri.so: wrong ELF class: ELFCLASS64)

It's trying to load /usr/lib/dri/... and finding 64-bit versions, and choking.  My question is, what program/library/whatever is trying to load these files, and why is it failing?  /usr/lib32/dri... exists, and contains the same files.  Presumably, if they were found, this would be working...so what package is at fault?  libGL?  ia32-libs?  OpenDriver (what is that?)  The application itself?  Or am I somehow doing it wrong?

---


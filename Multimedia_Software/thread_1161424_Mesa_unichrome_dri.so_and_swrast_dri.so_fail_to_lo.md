---
title: "Mesa unichrome_dri.so and swrast_dri.so fail to load"
date: 2009-05-16
forum: Multimedia Software
---

### Post by opticode on 2009-05-16
I have Jaunty Jackalope installed on my system with VIA CX700M integrated graphics and I can't seem to enable DRI.
When I run glxinfo with LIBGL_DEBUG=verbose I get the following error. Anybody have any ideas on how to resolve the issue?

name of display: :0.0
libGL: XF86DRIGetClientDriverName: 5.0.0 unichrome (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/unichrome_dri.so
libGL error: dlopen /usr/lib/dri/unichrome_dri.so failed (/usr/lib/dri/unichrome_dri.so: undefined symbol: _glapi_tls_Context)
libGL error: unable to load driver: unichrome_dri.so
libGL: OpenDriver: trying /usr/lib/dri/swrast_dri.so
libGL error: dlopen /usr/lib/dri/swrast_dri.so failed (/usr/lib/dri/swrast_dri.so: undefined symbol: _glapi_tls_Context)
libGL error: unable to load driver: swrast_dri.so
libGL error: reverting to indirect rendering
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

---

### Post by unknown_killer on 2009-06-05
I too am having problem with rendering. I have ViA K8M890.

only difference is tht i get swast_dri.so failed as it doesnt exist. No such file or directory! :(
Somebody have solution to this. Or where do i get this missing file??

---


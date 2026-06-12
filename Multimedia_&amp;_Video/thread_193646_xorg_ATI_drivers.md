---
title: "xorg ATI drivers"
date: 2006-06-10
forum: Multimedia &amp; Video
---

### Post by magi on 2006-06-10
Hi all,
I've got one of the older ATI cards a r280 chipset one and as reported elsewhere DRI stopped working using the fglrx drivers. I tried uninstalling them and reinstalling libgl1-mesa-dri and libgl1-mesa to use the xorg ATI drivers. Still no DRI.
 LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 5.0.3 r200 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/r200_dri.so
libGL error: dlopen /usr/lib/dri/r200_dri.so failed (/usr/lib/dri/r200_dri.so: undefined symbol: _glapi_get_dispatch)
libGL error: unable to find driver: r200_dri.so
libGL: XF86DRIGetClientDriverName: 5.0.3 r200 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/r200_dri.so
libGL error: dlopen /usr/lib/dri/r200_dri.so failed (/usr/lib/dri/r200_dri.so: undefined symbol: _glapi_get_dispatch)
libGL error: unable to find driver: r200_dri.so
display: :0  screen: 0
direct rendering: No

however, from /var/log/Xorg.0.log
(II) RADEON(0): Direct rendering enabled

any suggestions?
cheers
magi

---


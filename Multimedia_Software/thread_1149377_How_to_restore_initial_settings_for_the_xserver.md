---
title: "How to restore initial settings for the xserver?"
date: 2009-05-05
forum: Multimedia Software
---

### Post by Oenologist on 2009-05-05
I seem to have a serious problem with my Jaunty & Intel. My system got into some strange config and any attempt of enabling desktop effects, both in KDE and Gnome, ends in a total crash with green/pink glitches instead of the properly working X server (and TTYs).

I filled the bug form and got some diagnostic info from those guys, but still I was not provided with a solution to my problem. 

More details: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/364479](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/364479)

One of the examples of screen glitches: [http://launchpadlibrarian.net/25813795/21-04-09_1045.jpg](http://launchpadlibrarian.net/25813795/21-04-09_1045.jpg)

The system is unable to load dri:

sudo LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 1.9.0 i965 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/lib/dri/i965_dri.so
libGL error: dlopen /usr/lib/dri/i965_dri.so failed (/usr/lib/dri/i965_dri.so: undefined symbol: drm_intel_bo_alloc_for_render)
libGL error: unable to load driver: i965_dri.so
libGL: OpenDriver: trying /usr/lib/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/dri/swrast_dri.so


Should you need any other info regarding my config, I'll provide it ASAP.

What I mostly ask for is a quick guide concerning the reinstallation of the graphic server and its config to the standard, initial state (as found while conducting a clean install).

---


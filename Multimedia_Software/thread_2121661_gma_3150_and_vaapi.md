---
title: "gma 3150 and vaapi"
date: 2013-03-02
forum: Multimedia Software
---

### Post by revilar on 2013-03-02
I try to install vaapi on clear system, but hve a litle problem/
libva: VA-API version 0.32.0
libva: User requested driver 'i965'
libva: Trying to open /usr/lib/i386-linux-gnu/dri/i965_drv_video.so
vainfo: intel_driver.c:58: intel_driver_init: Assertion `dri_state->driConnectedFlag == VA_DRI2 || dri_state->driConnectedFlag == VA_DRI1' failed.

Early download and compile xf86-video-intel, Libdrm, Libvam, vaapi intel-driver, Cairo, Xserver.
What should I do, or what I do wrong?

Ubuntu 12.04, Atom n455. Dell Mini inspirion 1018.

P.S sorry for bad english, i am from russia.

---

### Post by revilar on 2013-03-03
In /etc/environment manually set:
LIBVA_DRIVER_NAME="i965"
LIBVA_DRIVERS_PATH="/usr/lib/i386-linux-gnu/dri"

Because if I type the command vainfo, it tells me that he can not find a driver i915_drv_video.so
And in the folder /usr/lib/i386-linux-gnu/dri have only i915_video.so

---

### Post by martin-juhl on 2013-04-22
I have the same problem on similar hardware..

Anyones got an answer???

---


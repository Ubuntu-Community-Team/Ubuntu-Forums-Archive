---
title: "Using fglrx, but really really slow"
date: 2007-03-28
forum: Multimedia &amp; Video
---

### Post by endfx on 2007-03-28
I've installed the fglrx driver and updated the xorg.conf file to use the fglrx driver.
Everything seems to work: Good resolution and sharp picture.

But running glxgears is super slow and running fgl_glxgears doesn't run at all with
the following error:
Using GLX_SGIX_pbuffer
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  30
  Current serial number in output stream:  30


I have dri and glx enabled in xorg.conf

Any ideas?

My card is an ATI x550.

Thanks.

---


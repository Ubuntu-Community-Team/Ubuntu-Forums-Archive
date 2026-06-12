---
title: "VA support for Intel X3100 chipset"
date: 2010-11-29
forum: Multimedia Software
---

### Post by patrickslee on 2010-11-29
I did a fresh install of Ubuntu 10.10 64 bit on a Dell Vostro 1510 laptop.

The result is amazing, everything just works. Out of curiosity I wanted to try hardware acceleration for videos.

I know X3100 only supports VA for MPEG2. But it's better than nothing. So I installed i965-va-driver and vainfo. libva1 is already installed.

Running vainfo gives the following:

```

libva: libva version 0.31.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/i965_drv_video.so
libva error: /usr/lib/dri/i965_drv_video.so init failed
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```

Looking at the change logs for libva there is a line says "Don't build i965 driver on non-i386 or non-amd64 architectures." which means i965 support is enabled.

Googling around doesn't give me any useful information.

Anyone has any clue about this?

---

### Post by grege on 2010-11-29
It will not work for a X3100, it only works for X4500 or newer and Nvidia and AMD with non-free drivers and a few obscure chips like GMA500 and S3.

You are stuck with XVideo acceleration, which is fine for most avi playback.

---

### Post by patrickslee on 2010-11-29
well that sucks. I thought X3100 is supported because of the driver name (i965). That's a bit confusing isn't it?

It seems XvMC is supported though. However neither gstreamer nor vlc support it.

---


---
title: "DirectFB: Error while playing mplayer without x11"
date: 2012-06-20
forum: Multimedia Software
---

### Post by newbie15 on 2012-06-20
I've used an older version of mplayer and tried compiling it without x11 option, compile and install has succeeded.

But when i tried to play a video file, its giving the error as below. Please help me in this regard. Thanks in advance.

```
root@localhost:~/mplayer-1.0~rc3++final.dfsg1# ./mplayer /tmp/mplayer/bin/Song1.mpeg

MPlayer 1.0rc3-4.4.5 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /tmp/mplayer/bin/Song1.mpeg.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [avc1]  640x360  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
commandline read: mplayer
commandline read: /tmp/mplayer/bin/Song1.mpeg

   ~~~~~~~~~~~~~~~~~~~~~~~~~~| DirectFB 1.2.10 |~~~~~~~~~~~~~~~~~~~~~~~~~~
        (c) 2001-2008  The world wide DirectFB Open Source Community
        (c) 2000-2004  Convergence (integrated media) GmbH
      ----------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2010-06-30 18:37)
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system_core' core!
    --> Initialization error!
[VO_SDL] SDL initialization failed: DirectFBCreate: Initialization error!.
Can't open /dev/fb0: No such file or directory
[fbdev2] Can't open /dev/fb0: No such file or directory
[svgalib: allocated virtual console #9]
```

---


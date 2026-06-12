---
title: "video, mplayer"
date: 2010-03-02
forum: Multimedia Software
---

### Post by cucuru on 2010-03-02
Hello, I have a problem with mplayer, when I try to execute a video file I have this:

```

admin@wimax-server:/usr/local/movies$ mplayer sample_100kbit.mp4
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing sample_100kbit.mp4.
libavformat file format detected.
[lavf] Audio stream found, -aid 0
[lavf] Video stream found, -vid 1
VIDEO:  [mp4v]  192x242  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
vo: couldn't open the X11 display ()!
[vdpau] Could not open dynamic library libvdpau.so.1
vo: couldn't open the X11 display ()!
VO XOverlay need a subdriver
[gl] using extended formats. Use -vo gl:nomanyfmts if playback fails.
vo: couldn't open the X11 display ()!
vo: couldn't open the X11 display ()!
vo: couldn't open the X11 display ()!
commandline read: mplayer
commandline read: sample_100kbit.mp4

   ~~~~~~~~~~~~~~~~~~~~~~~~~~| DirectFB 1.2.7 |~~~~~~~~~~~~~~~~~~~~~~~~~~
        (c) 2001-2008  The world wide DirectFB Open Source Community
        (c) 2000-2004  Convergence (integrated media) GmbH
      ----------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2009-06-02 06:26) 
(*) Direct/Memcpy: Using Generic 64bit memcpy()
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system_core' core!
    --> Initialization error!
[VO_SDL] SDL initialization failed: DirectFBCreate: Initialization error!.
Can't open /dev/fb0: No such file or directory
[fbdev2] Can't open /dev/fb0: No such file or directory
svgalib: Cannot get I/O permissions.

```

thanks! regards!

---

### Post by cucuru on 2010-03-02
I found the solution, i have to execute mplayer -vo x11 file

Does it exist anyway to avoid write it everytime? I mean, some configuration to say that it's the default option.

Thanks! regards

---

### Post by srix on 2010-03-02
Yes, look in /etc/mplayer/ or $HOME/.mplayer/ - one of the conf files should have an entry like "vo=x11,xv". If it is commented, uncomment and change it to x11 (or whatever works best for you).

---

### Post by cucuru on 2010-03-02
Thanks! it is in /etc/mplayer/mplayer.conf

Regards

---


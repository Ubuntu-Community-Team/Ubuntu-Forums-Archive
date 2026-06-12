---
title: "mplayer /dev/fb0"
date: 2010-03-01
forum: Multimedia Software
---

### Post by cucuru on 2010-03-01
hello, I'm trying to use mplayer in a server (ubuntu server 9.10) the rtsp server i'm using is Darwin streaming server.

I'm also using mplayer in other devices (ubuntu server 8.04) and it works perfectly.

In the device with ubuntu server 9.10 I found this error:

```

admin@wimax-server:~$ mplayer rtsp://192.168.12.1/sample_100kbit.mp4
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing rtsp://192.168.12.1/sample_100kbit.mp4.
Resolving 192.168.12.1 for AF_INET6...
Couldn't resolve name for AF_INET6: 192.168.12.1
Connecting to server 192.168.12.1[192.168.12.1]: 554...
A single media stream only is supported atm.
rtsp_session: unsupported RTSP server. Server type is 'DSS/6.0.3 (Build/526.3; Platform/Linux; Release/Darwin Streaming Server; State/Development; )'.
STREAM_LIVE555, URL: rtsp://192.168.12.1/sample_100kbit.mp4
Stream not seekable!
 file format detected.
Initiated "video/MP4V-ES" RTP subsession on port 54866
Initiated "audio/MPEG4-GENERIC" RTP subsession on port 33442
demux_rtp: Guessed the video frame rate as 15 frames-per-second.
    (If this is wrong, use the "-fps <frame-rate>" option instead.)
VIDEO:  [mp4v]  0x0  0bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
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
commandline read: rtsp://10.10.12.1/sample_100kbit.mp4

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

I look into /dev and I havent any fb0 file, what does it means? how can I solve it?

Thanks! regards

---


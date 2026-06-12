---
title: "After a player crash, video won't play in any player"
date: 2008-09-17
forum: Multimedia Software
---

### Post by velinion on 2008-09-17
I am running Ubuntu 8.04 x64 with Kubuntu-Desktop installed on top, currently using gdm and running in KDE. I use a Radion X1900XTX with drivers installed by EnvyNG about a month ago.

Video has been playing fine until, when clicking to play a video file, the computer crashed: Black screen, no sound, no video, CTRL-ALT-F2 didn't bring up a console, CTRL-ALT-BACKSPACE did nothing, as did CTRL-ALT-DEL and CTRL-C.

So I reset, and everything seemed to be working fine... until I tried to play another video. Video will no longer play in any video player. Most video platers quit on startup (Movie Player, mplayer, VLC). Kaffeine will play sound, but the video is black.
Kaffine outputs no errors to console, but VLC does, so the message is below.

Here is the error output by VLC
```

VLC media player 0.8.6e Janus
[00000345] pulse audio output error: Failed to connect to server: Connection refused
[00000345] pulse audio output error: Pulse initialization failed
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Value in failed request:  0x1a00006
  Serial number of failed request:  89
  Current serial number in output stream:  90

```

Here is the error output by mplayer
```

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Phenom(tm) 9600 Quad-Core Processor (Family: 16, Model: 2, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Buffy - 321 - Graduation Day Part 1.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [DIV3]  640x480  24bpp  25.000 fps  1007.8 kbps (123.0 kbyte/s)
Clip info:
 Software: Nandub v1.0rc2
 Name: Buffy.S03E21.DVDRip.DivX-HOSTiLE
 Subject: Buffy.S03E21.DVDRip.DivX-HOSTiLE
 Artist:
 Copyright:
 Comments:
xscreensaver_disable: Could not find XScreenSaver window.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffdivx] vfm: ffmpeg (FFmpeg DivX ;-) (MS MPEG-4 v3))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 32.0 kbit/2.08% (ratio: 4000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Planar YV12
X11 error: BadValue (integer parameter out of range for operation)

```
Note the last line repeats until ctrl-c is used to kill mplayer.

---

### Post by eye208 on 2008-09-17
Apparently the error occurs while initializing the XVideo overlay. It seems the crash left some part of the driver in a broken state.

You can probably work around the problem by using the OpenGL overlay or X11 software rendering to watch videos. However, the driver seems to be unstable anyway. Crashes like these should not happen at all.

What about Ubuntu's default restricted ATI driver? Doesn't it support your card?

---

### Post by velinion on 2008-09-18
Thanks for the info. Using it I did a bit of research and thought I'd post the results here in case anyone else has similar problems.

The crash was apparently the result of a known bug in the proprietary ATI 8-6 drivers which caused problems (XServer fails when playing media files with XVideo enabled.)

This bug is listed as resolved in the ATI 8-8 drivers.

Upgrading to the 8-8 drivers has also allowed my system to play videos again. Yay!

As for why I am using proprietary drivers, from what I understand, they are necessary for hardware accelerated 3d. I know glxgears reports a far higher framerate with the ATI drivers than with the Ubuntu default.

---

### Post by eye208 on 2008-09-19
> **velinion said:**
> As for why I am using proprietary drivers, from what I understand, they are necessary for hardware accelerated 3d.
I am not asking why you are using proprietary drivers. Pretty much everyone uses them.

I am asking why you are not using the proprietary driver **that comes with Ubuntu by default** (System -> Administration -> Restricted Drivers). Is there a particular reason why you have to use untested bleeding-edge drivers?

---

### Post by velinion on 2008-09-19
> **eye208 said:**
>  Is there a particular reason why you have to use untested bleeding-edge drivers?

I suppose there is no reason a *have* to use them, however,

> 
I know glxgears reports a far higher framerate with the ATI drivers than with the Ubuntu default


I do *benefit* from using them by getting a better framerate in games. Although given this experience, I may have to re-weigh the benefits versus the potential loss of stability.

---


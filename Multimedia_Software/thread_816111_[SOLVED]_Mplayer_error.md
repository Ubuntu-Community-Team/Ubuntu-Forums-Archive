---
title: "[SOLVED] Mplayer error"
date: 2008-06-02
forum: Multimedia Software
---

### Post by peakshysteria on 2008-06-02
Mplayer will not play files anymore. I get this:
```
Error opening/initializing the selected video_out ( -vo) device.
```

I've tried to reinstall via synaptic but no luck.

---

### Post by aeiah on 2008-06-02
have you recently started using compiz or restricted graphics drivers or something? i get that kind of error by default when i have compiz etc running.

the easiest thing to do is to open gmplayer
```
gmplayer
```

and go into options and select a video output device that works. i cant remember which one it'll be

---

### Post by peakshysteria on 2008-06-02
No restricted drivers. No compiz. Same error via terminal. But using gmplayer command in terminal the output is then visible as:
```
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 31, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/peaks/torrents/Gormenghast/Gormenghast Episode 1.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  704x384  24bpp  25.000 fps  988.5 kbps (120.7 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   6.2 (06.2) of 31706.3 ( 8:48:26.3)  0.8%                                   

MPlayer interrupted by signal 11 in module: seek
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

```

Beats me...

---

### Post by aeiah on 2008-06-02
all the screensaver and lirc errors and stuff you can ignore. its also reading your video and audio fine, so it isnt a codec issue. this is the important bit:

```
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
Error opening/initializing the selected video_out (-vo) device.

```

when you launch gmplayer (without a video file) you should be able to right click the application and go to the configuration / options / properties / whatever its called. you should be able to find a video output section and a list of possible outputs. one of them will be the right one. it may be x11 (which it suggests) or something else on the list. trial and error is the only advice i can give you since im not on ubuntu right now and dont know what the list will show and which is most likely to work.

---

### Post by peakshysteria on 2008-06-02
Thanks a million man. It worked. gmplayer (in terminal) --> rightclick --> Preferences --> video and it worked on the first try. No it works both via terminal and applications :)

Damn strange. But it's no big deal as long as it's working again....

---


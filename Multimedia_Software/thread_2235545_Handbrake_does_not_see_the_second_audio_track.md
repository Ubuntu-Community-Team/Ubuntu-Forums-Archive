---
title: "Handbrake does not see the second audio track"
date: 2014-07-21
forum: Multimedia Software
---

### Post by foxy123 on 2014-07-21
I am trying to rip a DVD with a foreign movie (Japanese) and Handbrake could see only English track. What I want is to rip the movie in the original language with English subtitles. Any help?

---

### Post by foxy123 on 2014-07-22
Well, it looks like the problem is wider. I cannot play DVDs. At least the ones I have tried. libdvdcss2 is installed but all players give me errors.

VLC gives me: ```
[0x7f20500009b8] main input error: ES_OUT_RESET_PCR called
[0x7f20500009b8] main input error: ES_OUT_RESET_PCR called
[0x7f20500009b8] main input error: ES_OUT_RESET_PCR called
[0x7f20500009b8] main input error: ES_OUT_RESET_PCR called
```

Mplayer ```
~$ mplayer /dev/sr0
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/sr0.
libavformat version 54.20.4 (external)
Mismatching header version 54.20.3
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  2000.0 kbps (250.0 kbyte/s)
Load subtitles in /dev/
Failed to open VDPAU backend libvdpau_i965.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 54.35.0 (external)
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
Audio: no sound
Starting playback...
Unsupported AVPixelFormat 53
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12 
[mpeg2video @ 0x7fed80837a20]warning: first frame is no keyframe
V:   0.8  15/ 15  7%  3%  0.0% 0 0 


Exiting... (End of file)

```

Even regionset ```
~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.

```

---


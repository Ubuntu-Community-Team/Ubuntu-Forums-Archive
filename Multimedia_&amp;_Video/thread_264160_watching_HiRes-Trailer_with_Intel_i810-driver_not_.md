---
title: "watching HiRes-Trailer with Intel i810-driver not possible?"
date: 2006-09-24
forum: Multimedia &amp; Video
---

### Post by loko on 2006-09-24
Hello,

i try to watch the HiRes(HighDefinition)-Trailer from Crysis, but i get a error. The screen keeps blue, with xine and also with mplayer. I noticed this with several HD-Stuff before, but now i want to ask if there is a solution.

mplayer gives me the following output:

```
user@w5f-laptop:/home/work/share$ mplayer www.deluxeBits.to...Crysis-Trailer-2006.wmv
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel  (Family: 6, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing www.deluxeBits.to...Crysis-Trailer-2006.wmv.
ASF file format detected.
VIDEO:  [WMV3]  1280x720  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening audio decoder: [dmo] Win32/DMO decoders
======= WAVE Format =======
Format Tag: 354 (0x162)
Channels: 2
Samplerate: 44100
avg byte/sec: 15323
Block align: 5945
bits/sample: 24
cbSize: 18
Unknown extra header dump: [18] [0] [3] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [e0] [0] [0] [0]
===========================
======= WAVE Format =======
Format Tag: 1 (0x1)
Channels: 2
Samplerate: 44100
avg byte/sec: 176400
Block align: 4
bits/sample: 16
cbSize: 0
===========================
GetOutput r=0x0   size:24576  align:1
StreamCount r=0x0  1  1
AUDIO: 44100 Hz, 2 ch, s16le, 122.6 kbit/8.69% (ratio: 15323->176400)
Selected audio codec: [wma9dmo] afm: dmo (Windows Media Audio 9 DMO)
==========================================================================
==========================================================================
Opening video decoder: [dmo] DMO video codecs
Creating new registry
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:2764800  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 1280 x 720 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1280x720 => 1280x720 Planar YV12
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 44100 Hz/2 channels/4 bpf/60208 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Starting playback...
aspect: Warning: no suitable new res found!
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm closed
user@w5f-laptop:/home/work/share$
```


so what can i do?

i have Intel 950GM graphic-chipset, so i use the i810-driver.
every other videos work very well.

is there a solution of getting HD-videos to work with this driver?

---

### Post by loko on 2006-09-24
i found out, that if i try ```
mplayer -vo x11 ...
``` i can watch the video. so maybe it is an xv-problem.

but i do not know excatly, can anyone help me out?

---


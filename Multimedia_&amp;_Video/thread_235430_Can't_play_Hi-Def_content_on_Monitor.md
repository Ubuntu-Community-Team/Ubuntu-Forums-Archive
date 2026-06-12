---
title: "Can't play Hi-Def content on Monitor"
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by deadite66 on 2006-08-13
i'm having trouble playing hi-def files.

**X11 error: BadAlloc (insufficient resources for operation)?,?% 1 0**
suggests a xorg problem, the files will play fine on a vnc from the same pc

anything i can do?

```
MPlayer 1.0pre7try2-3.4.5 (C) 2000-2005 MPlayer Team
CPU: Intel  (Family: 6, Stepping: 8)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Playing mallard.m2t.
TS file format detected.
DEMUX OPEN, AUDIO_ID: -1, VIDEO_ID: -1, SUBTITLE_ID: -1,
PROBING UP TO 2000000, PROG: 0
VIDEO MPEG2(pid=17)NO AUDIO!  NO SUBS (yet)!  PROGRAM N. 0
Opened TS demuxer, audio: ffffffff(pid -1), video: 10000002(pid 17)...POS=0
VIDEO:  MPEG2  1440x1080  (aspect 3)  25.000 fps  25000.0 kbps (3125.0 kbyte/s)
vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0" => local display)
Opening video filter: [cropdetect]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 1440 x 1080 (preferred csp: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm:libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 1440 x 1080 (preferred csp: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1440x1080 => 1920x1080 Planar YV12  [fs]
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
X11 error: BadAlloc (insufficient resources for operation)


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

-----------------------------------------------------------------------------------------

MPlayer 1.0pre7try2-3.4.5 (C) 2000-2005 MPlayer Team
CPU: Intel  (Family: 6, Stepping: 8)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Playing Robotica_1080.wmv.
ASF file format detected.
VIDEO:  [WMV3]  1440x1080  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening audio decoder: [dmo] Win32/DMO decoders
======= WAVE Format =======
Format Tag: 354 (0x162)
Channels: 6
Samplerate: 48000
avg byte/sec: 48000
Block align: 8192
bits/sample: 24
cbSize: 18
Unknown extra header dump: [18] [0] [3f] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [e0] [0] [0] [0]
===========================
======= WAVE Format =======
Format Tag: 1 (0x1)
Channels: 2
Samplerate: 48000
avg byte/sec: 192000
Block align: 4
bits/sample: 16
cbSize: 0
===========================
GetOutput r=0x0   size:73728  align:1
StreamCount r=0x0  1  1
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [wma9dmo] afm:dmo (Windows Media Audio 9 DMO)
==========================================================================
vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0" => local display)
Opening video filter: [cropdetect]
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:4665600  align:1
StreamCount r=0x0  1  1
Decoder supports the following YUV formats: YV12 YUY2 UYVY YVYU   â–’
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 1440 x 1080 (preferred csp: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1440x1080 => 1440x1080 Planar YV12  [fs]
Selected video codec: [wmv9dmo] vfm:dmo (Windows Media Video 9 DMO)
==========================================================================
Checking audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
AF_pre: 48000Hz/2ch/s16le
alsa-init: 1 soundcard found, using: default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bps)
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
Starting playback...
X11 error: BadAlloc (insufficient resources for operation)?,?% 1 0


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm closed   
```

---

### Post by deadite66 on 2006-08-13
hmm from the ogle faq looks like i need to increase shared graphics memory in bios.

> 42. I get a weird error "BadAlloc" when Ogle tries to open a DVD, why?

   X Error of failed request:  BadAlloc (insufficient resources for operation)
     Major opcode of failed request:  141 (XVideo)
     Minor opcode of failed request:  19 ()
     Serial number of failed request:  56
     Current serial number in output stream:  56

It means that there is not enough graphics memory. Older laptops often only have 2-3 megabytes of graphics memory. It might also be an issue if you are using a high resolution or have direct rendering / 3D support enabled that allocates memmory (for some cards/drivers).

There are two main ways to free up more memory: One is turn off the pixmap cache, and the other is to reduce the resolution or colour depth of your display. In order to do this, you have to edit your configuration file (on my machine it is at /etc/X11/XF86Config-4), and restart X Windows. The following example shows what I did: 

---


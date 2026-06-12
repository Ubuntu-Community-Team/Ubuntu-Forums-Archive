---
title: "Added montior, now video doesn't work"
date: 2006-11-25
forum: Multimedia &amp; Video
---

### Post by Nachtengel on 2006-11-25
I recently got a nice 22" LCD and have gotten it set up, changing the x.org.conf file to get the full 1600x1050 resolution out of it.  However, in doing so, no video files will play... Mplayer, VLC, movie player... they all crash.  I was wondering if anyone had any idea as to what would cause this, where to start looking, and what can be done.

---

### Post by Nachtengel on 2006-11-27
Did some more digging around:
```

user@host:~$ mplayer ~/vidfile.mpg
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 X2 Manchester,Toledo (Family: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
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
Playing /home/user/vidfile.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG1  352x240  (aspect 12)  59.940 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 32000 Hz, 2 ch, s16le, 112.0 kbit/10.94% (ratio: 14000->128000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 352 x 240 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 32000Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 32000 Hz/2 channels/4 bpf/43688 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 32000Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 32000Hz/2ch/s16le -> 32000Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 352 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 352x240 => 352x264 Planar YV12
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm closed

```

 Any ideas?

---

### Post by Nachtengel on 2006-12-25
Fixed... found that I wasn't running nvidia's drivers like I thought I was.  Installed nvidia-glx like I thought I had already and the SLI configuration was able to render the newer 1600x1440 resolution just fine.

---


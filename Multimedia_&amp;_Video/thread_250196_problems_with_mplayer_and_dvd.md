---
title: "problems with mplayer and dvd"
date: 2006-09-03
forum: Multimedia &amp; Video
---

### Post by farno on 2006-09-03
i installed mplayer from repositories
i have a problem when i want to watch dvd: i see only the introduction on dvd (the page of copyright) and after that mplayer closes
i've already installed libdvdread3 and css
is somebody able to help me?

---

### Post by ispmarin on 2006-09-03
Did you ran the script at /usr/share/doc/libdvdread3/css? Try to open the mplayer from a terminal and look for the error message.

---

### Post by farno on 2006-09-03
yes i did
the output of
mplayer dvd:// is
```
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices  (Family: 15, Stepping: 2)
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
Playing dvd://.
libdvdread: Using libdvdcss version 1.2.5 for DVD access
Reading disc structure, please wait...
There are 4 titles on this DVD.
There are 1 chapters in this DVD title.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000018b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000254
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00001936
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00001983
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00002a6c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00002ab9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00002af4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00002b41
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
DVD successfully opened.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  9000.0 kbps (1125.0 kbyte/s)
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
AC3: 2.0 (stereo)  48000 Hz  224.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12
alsa-space: xrun of at least 0.114 msecs. resetting stream5.5% 15 0
A:  21.2 V:  21.6 A-V: -0.472 ct: -0.033 536/536 16%  2%  5.5% 15 0
alsa-uninit: pcm closed

Exiting... (End of file)

```

in my opinion there is a problem with menu support
what do you think?

---

### Post by yopnono on 2006-09-03
> **farno said:**
> yes i did
the output of
mplayer dvd:// is

in my opinion there is a problem with menu support
what do you think?

Have you tried xine ? can it play your dvd

---

### Post by ispmarin on 2006-09-03
Maybe you are correct, because it loads all the codecs correctly, the file correctly... and just give a "end of file". Did you try to use xine or vlc?

---

### Post by farno on 2006-09-03
at the moment on my ubuntu i have:
1 totem-gstreamer (for audio and video files)
2 vlc (for dvd)
3 mplayer (for videos on the net)
i would use only one between mplayer and vlc:
i could uninstall vlc if mplayer is able to play dvd or i can uninstall mplayer if on between vlc and totem-gstreamer is able to play videos on the net
the problem is that vlc and totem-gstreamer are not able to play videos on the net
so i tried to use mplayer for dvd...
but with no results at the moment

---

### Post by whatever on 2006-09-03
> **farno said:**
> in my opinion there is a problem with menu support
mplayer does not (yet) support dvd menus.

---

### Post by farno on 2006-09-03
ok
so i think that this is the problem
thank's

---


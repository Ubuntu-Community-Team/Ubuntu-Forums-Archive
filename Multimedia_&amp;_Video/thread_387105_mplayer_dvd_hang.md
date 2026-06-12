---
title: "mplayer dvd hang"
date: 2007-03-17
forum: Multimedia &amp; Video
---

### Post by gaillard on 2007-03-17
Would someone mind looking at this output?

```

gaillard@gaillard-desktop:~$ mplayer dvd://
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3400+ (Family: 15, Model: 4, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


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
Reading disc structure, please wait...
There are 99 titles on this DVD.
There are 28 chapters in this DVD title.
There are 1 angles in this DVD title.
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x05
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x06
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:731
    for cell_position[i].zero_1 = 0x04
DVD successfully opened.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
AC3: 5.1 (3f+2r+lfe)  48000 Hz  448.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
alsa-init: using device default
alsa-lib: confmisc.c:670:(snd_func_card_driver) cannot find card '0'
alsa-lib: conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
alsa-lib: confmisc.c:391:(snd_func_concat) error evaluating strings
alsa-lib: conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
alsa-lib: confmisc.c:1070:(snd_func_refer) error evaluating name
alsa-lib: conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
alsa-lib: conf.c:3947:(snd_config_expand) Evaluate error: No such device
alsa-lib: pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default
alsa-init: playback open error: No such device
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 854x480 Planar YV12 
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 854x480 Planar YV12 
A:   5.6 V:   0.6 A-V:  5.004 ct:  0.029 162/160  3%  1%  5.6% 0 0 
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.
a52: CRC check failed!  3.428 ct:  1.671 557/554  6%  0%  2.0% 0 0 
a52: error at resampling
a52: CRC check failed!  3.479 ct:  1.675 558/555  6%  0% 21.4% 0 0 
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  

```



And those CRC failures go on and on... any idea what the problem is?
I just installed mplayer and ran the dvd restricted command...

---

### Post by gaillard on 2007-03-17
hmm bizarelly this only happens on a newer dvd of mine.  The stranger than fiction film.

Interesting, it is sony...

---

### Post by ninja67 on 2007-06-30
I got the same error. The DVD played perfectly with PowerDVD. I was just hoping to find out a solution for mplayer here. I did find out that mplayer could play the dvd once i seeked it to 10mins using the PgUp button. Then I started seeking towards the beginning, only to find that it wouldn't seek to below 3 mins. Luckily, that's when the starting credits end and the movie begins. Incidentally vlc couldn't play it as well. I was surprised.

---


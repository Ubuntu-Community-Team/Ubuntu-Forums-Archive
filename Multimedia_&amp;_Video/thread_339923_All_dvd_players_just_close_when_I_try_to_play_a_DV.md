---
title: "All dvd players just close when I try to play a DVD"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by PapaKoen on 2007-01-16
All the dvd players just stop (exit, quit, close) when I try to play a dvd
previous loggings: [http://www.ubuntuforums.org/showthread.php?t=339372]("http://www.ubuntuforums.org/showthread.php?t=339372")

The console for mplayer
papa@ubuntu:~$ sudo mplayer dvd://1 -dvd-device /dev/hdc
Password:
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron Covington/Pentium II Deschutes,Tonga/Pentium II Xeon (Family: 6, Model: 5, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled with runtime CPU detection.


Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing dvd://1.
Reading disc structure, please wait...
There are 40 titles on this DVD.
There are 11 chapters in this DVD title.
There are 1 angles in this DVD title.
DVD successfully opened.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  9800.0 kbps (1225.0 kbyte/s)
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
No accelerated IMDCT transform found
AC3: 2.0 (stereo)  48000 Hz  192.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such device.
[VO_3DFX] Unable to open /dev/3dfx.
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
alsa-init: using device default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12 
X11 error: BadAlloc (insufficient resources for operation)?,?% 2 0 


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm closed
papa@ubuntu:~$ 


Thanks for any tips

---

### Post by crispy_420 on 2007-01-19
Do you have libdvdcss installed? Maybe a video driver issue?

---

### Post by magli on 2007-02-04
Were you able to solve this? I am having the same problem on an old clamshell ibook which I just installed xubuntu on.

I have libdvdcss2 installed, and am having the same problem with gxine, ogle and vlc.

---

### Post by planC on 2007-11-16
I have a similar problem. mplayer opens and i have audio but no video, then .... nothing.
Don't know what to do.

---

### Post by frenchie091 on 2007-11-26
Hi,
I've been trawling the web trying to find a solution to this problem, and finally fixed it. As I understand it (I'm not a developer mind) the problem lies not with the individual players (obviously, since they're all crashing with the same error), but has something to do with how X11 and your video card's driver handle memory, particularly when it comes to higher resolution video like DVD. 

Following tips I came across here: [http://ubuntuforums.org/archive/index.php/t-194746.html]("http://ubuntuforums.org/archive/index.php/t-194746.html")
I first edited my xorg.conf and added these lines under the Device section corresponding to my video card:

        Option          "VideoRam" "65536"
        Option          "CacheLines" "1980"

Restarted X11, and still no joy. Kept searching, someone suggested adding this also:

        Option          "LinearAlloc" "8192"

Restarted X11, still didn't work. Then in the Screen section in xorg.conf, I changed the colour resolution to be 16 instead of 24:

        DefaultDepth    16

Restarted X11, and hey presto! DVDs play in xine, vlc, etc., and I am happy. I could go back and edit the xorg.conf, removing one of those edits at a time to see which one is responsible for fixing it, but I'm not going to, as I'm already sick of trying to fix this annoying problem and am just happy it works.

---


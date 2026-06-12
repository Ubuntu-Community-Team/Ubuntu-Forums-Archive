---
title: "blank window playing movies"
date: 2007-03-07
forum: Multimedia &amp; Video
---

### Post by kroiz on 2007-03-07
I get a blank window when playing a movies. both in totem and in vlc.
What can I do?

---

### Post by chewearn on 2007-03-07
Do you have Beryl running?  Some people reported that if Beryl is running, you change the VLC video output option to X11.

---

### Post by kroiz on 2007-03-07
> **AstalaVista said:**
> Do you have Beryl running?  Some people reported that if Beryl is running, you change the VLC video output option to X11.

I got Compiz, but it is not running. I can run it from the top menu.
a couple of months ago I followed a short tutorial for installing xgl and compiz.
but it did not work properly (only works on the left 1024 pixels of the screen).
think I should uninstall it?

---

### Post by panch0 on 2007-03-07
Try with MPlayer (KPlayer is a good frontend), and the video output should be XVideo (-vo xv). If it doesn't work, post the log you get.

---

### Post by kroiz on 2007-03-08
> **panch0 said:**
> Try with MPlayer (KPlayer is a good frontend), and the video output should be XVideo (-vo xv). If it doesn't work, post the log you get.
Like that ?
```
 mplayer -vo xv DSCF0299.avi
```and where can I find the log please.
when I run the above from the command line I get
```
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU:         Intel(R) Pentium(R) M processor 1600MHz (Family: 6, Model: 9, Stepping: 5)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
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

Playing DSCF0299.avi.
AVI file format detected.
VIDEO:  [MJPG]  640x480  24bpp  30.000 fps  9216.9 kbps (1125.1 kbyte/s)
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 16000 Hz, 1 ch, u8, 128.0 kbit/100.00% (ratio: 16000->16000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG decoder)
==========================================================================
alsa-init: using device default
alsa: 48000 Hz/1 channels/1 bpf/16384 bytes buffer/Unsigned 8 bit
AO: [alsa] 48000Hz 1ch u8 (1 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar 422P)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar 422P as output csp (no 1)
Movie-Aspect is undefined - no prescaling applied.

SwScaler: BICUBIC scaler, from Planar 422P to Planar YV12 using MMX2
VO: [xv] 640x480 => 640x480 Planar YV12 
A:   0.1 V:   0.0 A-V:  0.122 ct:  0.000   1/  1 ??% ??% ??,?% 0 0 
alsa-uninit: pcm closed

Exiting... (End of file)

```

But still the same blank screen

---

### Post by panch0 on 2007-03-09
That's the log you posted right there!

MJPEG codec is kinda weird, haven't seen that in an AVI. But why not...

Anyway, please run

mplayer -v -vo xv DSCF0299.avi

and post the output.

---

### Post by kroiz on 2007-03-19
That is the thread that helped me:
[http://ubuntuforums.org/showthread.php?t=383106](http://ubuntuforums.org/showthread.php?t=383106)

---


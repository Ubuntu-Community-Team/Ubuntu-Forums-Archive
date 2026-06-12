---
title: "Mplayer crashing?"
date: 2006-11-22
forum: Multimedia &amp; Video
---

### Post by SmiLey497 on 2006-11-22
When i try to open a movie in mplayer a little window pops-up and disappears at exactly the same time but the audio plays.

this is the code i get when i run it in the terminal

> ~$ gmplayer
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 4000+ (Family: 15, Model: 39, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.



Xlib:  extension "XFree86-VidModeExtension" missing on display "localhost:1.0".
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
Xlib:  extension "XFree86-VidModeExtension" missing on display "localhost:1.0".

and when the video plays this shows up

> libavformat file format detected.
VIDEO:  [FLV1]  320x240  0bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Trying to force audio codec driver family ffmpeg...
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 1 ch, s16le, 0.0 kbit/0.00% (ratio: 0->44100)
Selected audio codec: [ffmp3] afm: ffmpeg (FFmpeg MPEG layer-3 audio decoder)
==========================================================================
==========================================================================
Trying to force video codec driver family vfw...
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffflv] vfm: ffmpeg (FFmpeg Flash video)
==========================================================================
alsa-init: using device default
alsa: 48000 Hz/1 channels/2 bpf/32768 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 1ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 320x240 => 320x240 Planar YV12 
A:   6.6 V:   6.6 A-V: -0.003 ct:  0.006 199/199  4% 12%  1.4% 5 0

---

### Post by SmiLey497 on 2006-11-22
bump

---

### Post by SmiLey497 on 2006-11-22
bueller?

---

### Post by SmiLey497 on 2006-11-22
anybody

---

### Post by SmiLey497 on 2006-11-23
?

---

### Post by SmiLey497 on 2006-12-02
anybody

---

### Post by CarpKing on 2006-12-03
So the video and audio still work fine?  Then it's probably nothing to worry about.  The terminal output looks fine too.  Not sure why the window comes up, but I have it sometimes too.

---

### Post by SmiLey497 on 2006-12-05
no. no video shows at all only audio plays, the video screen pops up and then disappears

---

### Post by SmiLey497 on 2006-12-05
only full screen works but nothing else

---


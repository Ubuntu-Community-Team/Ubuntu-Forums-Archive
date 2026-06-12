---
title: "Can't open videos, jackd related problem?"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by Nighto on 2008-01-27
Hi, i run Ubuntu since Breezy on my computers, and though not an advanced user, I think I'm no newbie either. However I just run in a problem that I have no idea what to do.

I just installed Ubuntu Gutsy on my girlfriend's laptop, an Acer Aspire 5720. When I try to open any video, Totem just pop and crash. 

When I try to run Totem on a terminal, that's what I got:

```
$ totem MVI_0254.AVI
sh: jackd: not found
sh: jackd: not found
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 48 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

I also tried with VLC and MPlayer, without success:

```
VLC media player 0.8.6c Janus
[00000291] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
No accelerated IMDCT transform found
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85
```

```
MPlayer 1.0rc2-4.1.3-DFSG-free (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Creating config file: /home/rapousa/.mplayer/config
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [Heijin] Love Hina 01 [DVDrip].mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3) "Dolby Digital 2.0", -aid 0, -alang jpn
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  720x544  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 544 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x544 => 726x544 Planar YV12 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
[...]
```

Does anybody have any clue of what's going on? Of course I have codecs installed, and I also tried other videos.

Thanks in advance.

---

### Post by hihihi on 2008-02-07
hi

my first question would be: did u install jack?

apt-get install jackd, libjack0 and libjack 0.100

on the other hand, al your players should run fine, once installed and they do not require jack... do you have alsa set up? and alsa-oss?? alsa-utils?

can u listen to music with rhythmbox?

cheers


ps: mplayer tells that your sound-device is bussy, perhaps u have some bad working program grabbing your soundcard? but i would bet u just need alsa-oss!?!

---

### Post by Nighto on 2008-02-07
> **hihihi said:**
> hi

my first question would be: did u install jack?

apt-get install jackd, libjack0 and libjack 0.100

No, i didn't. I run JACK sometimes for my recordings in Ardour using an M-Audio 2496, but that's not her case. I think that she shouldn't be forced to run jack just to see a video.
> **hihihi said:**
> 

on the other hand, al your players should run fine, once installed and they do not require jack... do you have alsa set up? and alsa-oss?? alsa-utils?

can u listen to music with rhythmbox?

cheers


ps: mplayer tells that your sound-device is bussy, perhaps u have some bad working program grabbing your soundcard? but i would bet u just need alsa-oss!?!

i didn't nothing at all. In a "stock" Ubuntu the videos just doesn't work. Can't see why, because all sound programs do work, such as Firefox with flash videos, and any music players such as Rhythmbox and Amarok.

So you bet that I need to install alsa-oss? I'll try that.

Thanks.

**EDIT:** It didn't work. Any other suggestions? Thanks.

---


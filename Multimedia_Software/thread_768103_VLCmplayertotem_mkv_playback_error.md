---
title: "VLC/mplayer/totem mkv playback error"
date: 2008-04-26
forum: Multimedia Software
---

### Post by itix on 2008-04-26
I have a movie clip in mkv which won't play. I tried it in all the three media players I have and none of them worked. It's just this particular MKV and the only significant difference between this one and a working mkv that I have is that the non-working has it's sound in AAC and the other are mpeg1 layer 3 (mp3). I don't think it is the sound though because you can sometimes hear about half a second of music in the beginning before it crashes.

output VLC:
```
VLC media player 0.8.6c Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  83
  Current serial number in output stream:  84

```

Totem output:
```
sh: jackd: not found
sh: jackd: not found
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 56 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

output Mplayer:
```
2:1.0~rc1-0ubuntu13.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Celeron(R) M processor 1.60GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing *****.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "*****", -vid 0
[mkv] Track ID 2: audio (A_AAC) "2.0 AAC", -aid 0, -alang jpn
[mkv] Track ID 3: subtitles (S_TEXT/***) "***", -sid 0, -slang eng
[mkv] Track ID 4: subtitles (S_TEXT/UTF8) "SRT", -sid 1, -slang eng
[mkv] Will play video track 1
Matroska file format detected.
VIDEO:  [avc1]  1280x720  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't
  and won't help unless you provide this information when reporting a
  possible bug. 
gnome_screensaver_control()
```

EDIT: ***** = my file path
      *** = the curse A-S-S which was included in the output...

---

### Post by stek79 on 2008-04-26
Hi,
 same problem here. I'm using Hardy up-to-date.

It seems to be a quite common problem, I've read that some have solved it (xorg bug?). Regarding my self, I still have to live with it - I can get rid of it disabling compiz, though.

If you use mplayer -vo x11 , you should be able to view your clip, but with a huge CPU utilization penalty.

Anyone knows how to solve that?

---

### Post by itix on 2008-04-30
An update:
The file mentioned plays on my (1,5 days old =) Eee PC (EeeXubuntu) using totem and xine but I have no sound.
I'm suspecting missing libraries.

Info on file:
Dimensions: 1280 x720
Codec: H264
Audio Codec: MPEG-4 AAC audio
Sample rate: 48 000 Hz

---

### Post by geoffree on 2009-11-23
I also have problem with Totem movie player crashing on contact. Although reported as a bug, and said to be solved, it isn't. One response was that it was the version which may be right, but is also pitiful in that it should have been fixed by now by the Ubuntu team if thats the case.

One strange action which may be significant: 
Cannot install 'gstreamer0.10-fluendo-mpegdemux' without removing 'gstreamer0.10-plugins-bad' and vice-versa. Is it significant?
I need a video player, but more, I (and all Ubuntu users) need to be able to find out how to fix such problems as soon as a fix is found rather than a clutter of suggestions. This is up to the managers of the Forum and Launchpad I believe. 

geoffree

---


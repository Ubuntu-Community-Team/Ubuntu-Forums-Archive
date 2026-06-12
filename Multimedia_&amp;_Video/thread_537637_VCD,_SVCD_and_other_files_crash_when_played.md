---
title: "VCD, SVCD and other files crash when played"
date: 2007-08-29
forum: Multimedia &amp; Video
---

### Post by linuksamiko on 2007-08-29
some video-codec is driving me crazy (I gues it is MPEG but I'm not sure, I'm not this much into the codec-stuff). When ever I open a video of this typ, I get a crash as soon the player wants to play.
I tried it with Xine, VLC, mplayer but all of them crash. I think that I have installed all requierd programs. I will attach the out put given by mplayer (since mplayer gives you the most information what is going on)

This happens for example with VCDs, SVCDs, films that I recorded with "recordmydesktop" or the elephantsdream HD-Version.
But DVD, XVID work fine.

I hope anybody got an idea.

```

CPU: Genuine Intel(R) CPU           T2300  @ 1.66GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing out.ogg.
[Ogg] stream 0: video (Theora v3.2.0), -vid 0
[Ogg] stream 1: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  1024x768  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x87f5f1c]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 1024 x 768 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 1024x768 => 1024x768 Planar YV12 
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 2 ch, s16le, 172.0 kbit/24.37% (ratio: 21497->88200)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.


```

---

### Post by push_harder on 2008-01-20
I have the same problem.
I went to play a video on youtube just after i installed ubuntu.
and i installed the general codec in the dialog that popped up.

Now, youtube video's play (very very laggy)
but totem and VLC crash as soon as i go to play a video or use visulisation with audio.

Any ideas??

Thanks in advance.

---


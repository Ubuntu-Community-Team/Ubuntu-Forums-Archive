---
title: "Can't play AVI video. Voxware decoder needed."
date: 2010-01-25
forum: Multimedia Software
---

### Post by alexthunder on 2010-01-25
I can't play my AVI movie in Linux since it needs Voxware decoder.
The video itself is shown just fine, but I can't hear any sound.

I tried Totem, VLC and MPlayer to no avail. I also tried to install gstreamer and ubuntu-restricted-extras, but wasn't able to solve my problem....

please help me

---

### Post by mc4man on 2010-01-25
If you have a 32 bit karmic then install w32codecs [from here]("http://packages.medibuntu.org/karmic/w32codecs.html"), then try mplayer from terminal to see ( mplayer /path/to/file

Should play some at least
> clipped....
Opening audio decoder: [dshow] Win32/DirectShow decoders
AUDIO: 44100 Hz, 2 ch, s16le, 96.1 kbit/6.81% (ratio: 12016->176400)
Selected audio codec: [voxware] afm: dshow (VoxWare)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...


---

### Post by alexthunder on 2010-01-26
> **mc4man said:**
> If you have a 32 bit karmic then install w32codecs [from here]("http://packages.medibuntu.org/karmic/w32codecs.html"), then try mplayer from terminal to see ( mplayer /path/to/file

Should play some at least
I had w32codecs installed already... but...

I wasn't able to play the video before, but after launching mplayer in the terminal, it started working just fine... 
```
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffdivx] vfm: ffmpeg (FFmpeg DivX ;-) (MSMPEG-4 v3))
==========================================================================
==========================================================================
Opening audio decoder: [dshow] Win32/DirectShow decoders
AUDIO: 44100 Hz, 2 ch, s16le, 96.1 kbit/6.81% (ratio: 12016->176400)
Selected audio codec: [voxware] afm: dshow (VoxWare)
==========================================================================
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 480 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 480x352 => 480x352 Planar YV12 
A:  33.3 V:  33.3 A-V:  0.000 ct: -0.001 833/833  1%  0%  1.0% 0 0 
Exiting... (Quit)
```
and SMPlayer started working as well.

Thank you!

---


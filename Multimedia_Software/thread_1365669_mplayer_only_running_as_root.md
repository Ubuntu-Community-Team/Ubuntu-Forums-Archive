---
title: "mplayer only running as root"
date: 2009-12-27
forum: Multimedia Software
---

### Post by atropa on 2009-12-27
I normally use

```
mplayer dvdnav://1
```

to watch DVDs on my laptop. Now I have the strange problem, that for some DVDs this doesn't work, i.e. mplayer outputs lots of error messages and only plays audio. I'm having this issue with Harry Potter 5. With

```
sudo mplayer dvdnav://1
``` it works though.

Technical details:
My laptop is an acer travelmate 8210 running ubuntu 9.10.
Graphics: ATI Radeon mobility X1600 with the opensource Radeon driver.
I use the lib*-extra-52 packages as codecs libraries, i.e.
*= avcodec, avformat, avdevice

Here the errors by mplayer:
```
DVDNAV, switched to title: 1
MPEG-PS file format detected.
VIDEO:  MPEG1  720x576  (aspect 3)  25.000 fps  7500.0 kbps (937.5 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1
Selected video codec: [ffmpeg1] vfm: ffmpeg (FFmpeg MPEG-1)
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
a52: CRC check failed!  
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
a52: error at resampling
[mpeg1video @ 0x7f84d7c12880]inter matrix damaged
[mpeg1video @ 0x7f84d7c12880]inter matrix damaged
a52: CRC check failed!  0.214 ct:  0.004   2/  2 ??% ??% ??,?% 0 0 
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
[mpeg1video @ 0x7f84d7c12880]sequence header damaged ??% ??,?% 0 0 
[mpeg1video @ 0x7f84d7c12880]Missing picture start code
[mpeg1video @ 0x7f84d7c12880]Missing picture start code
[mpeg1video @ 0x7f84d7c12880]Missing picture start code
[mpeg1video @ 0x7f84d7c12880]Missing picture start code
[mpeg1video @ 0x7f84d7c12880]Missing picture start code
[mpeg1video @ 0x7f84d7c12880]Missing picture start code
[mpeg1video @ 0x7f84d7c12880]Missing picture start code
[mpeg1video @ 0x7f84d7c12880]Missing picture start code
[mpeg1video @ 0x7f84d7c12880]Missing picture start code
```

Does anybody have an idea on this?

---

### Post by andrew.46 on 2009-12-27
Hi atropa,

Try both of the following as an ordinary user:

```

mplayer -vo xv dvdnav://
mplayer -vo x11 dvdnav://

```

Where does your copy of MPLayer come from?

Andrew

---

### Post by atropa on 2009-12-30
Thanks for your answer

Neither of the output drivers lets the dvd play or change the errors.

I got mplayer from the ubuntu repositories.

The only difference between the two disks I can see is, that batman is mpeg2
and Harry Potter is mpeg1.

---


---
title: "DVD doesn't want to play in Ubuntu"
date: 2010-06-14
forum: Multimedia Software
---

### Post by pmatos on 2010-06-14
Hi guys,

I have a live concert DVD which I wanted to rip to audio or even just to watch in my PC but it denies playing it. Even though I can play it pretty well on my PS3 or DVD Player.

If I try to rip it, I get:
```
pmatos@pm18pc01:~/Temp/westernhagen$ transcode -i /dev/dvd -x dvd -T 2,1,1 -a 0 -y ogg -m track1.ogg
transcode v1.1.5 (C) 2001-2003 Thomas Oestreich, 2003-2009 Transcode Team
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Using libdvdcss version 1.2.10 for DVD access
[dvd_reader.c] DVD title 2/3: 19 chapter(s), 1 angle(s), title set 2
[dvd_reader.c] title playback time: 01:13:57.18  4438 sec
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Using libdvdcss version 1.2.10 for DVD access
[dvd_reader.c] DVD title 2/3: 19 chapter(s), 1 angle(s), title set 2
[dvd_reader.c] title playback time: 01:13:57.18  4438 sec
[transcode] V: auto-probing     | /dev/dvd (OK)
[transcode] V: import format    | MPEG 2 program stream in DVD PAL (module=dvd)
[transcode] A: auto-probing     | /dev/dvd (OK)
[transcode] A: import format    | AC3 in DVD PAL (module=dvd)
[transcode] V: AV demux/sync    | (1) sync AV at initial MPEG sequence
[transcode] V: import frame     | 720x576  1.25:1  encoded @ 4:3
[transcode] V: bits/pixel       | 0.174
[transcode] V: decoding fps,frc | 25.000,3
[transcode] V: video format     | YUV420 (4:2:0) aka I420
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]
[transcode] A: export format    | 0x55    MPEG ES Layer 3 [48000,16,2]  128 kbps
[transcode] V: export format    | unknown (module dependant)
[transcode] V: encoding fps,frc | 25.000,3
[transcode] A: language         | de
[transcode] A: bytes per frame  | 7680 (7680.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32/AMD64 accel | sse3 sse2 sse mmx cmove asm 
[transcode] V: video buffer     | 10 @ 720x576 [0x2]
[transcode] A: audio buffer     | 10 @ 48000x2x16
[import_dvd.so] v0.4.1 (2007-07-15) (video) DVD | (audio) MPEG/AC3/PCM
[export_ogg.so] v0.0.5 (2003-08-31) (video) null | (audio) ogg
[encoder.c] warning: video codec not supported by export module
[transcode] critical: failed to init export modules
[transcode] critical: plug-in initialization failed
```

If I try to watch it with mplayer:
```
pmatos@pm18pc01:~/Temp/westernhagen$ mplayer /dev/dvd
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/dvd.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  2000.0 kbps (250.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] This driver only supports the 3Dfx Banshee, Voodoo3 and Voodoo 5.
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
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
a52: CRC check failed!  
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12 
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code% 11.1% 0 0 
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]00 motion_type at 34 2%  2% 10.3% 0 0 
[mpeg2video @ 0x7fdd6c4de9a0]00 motion_type at 17 30
[mpeg2video @ 0x7fdd6c4de9a0]Warning MVs not available
[mpeg2video @ 0x7fdd6c4de9a0]concealing 720 DC, 720 AC, 720 MV errors
[mpeg2video @ 0x7fdd6c4de9a0]00 motion_type at 6 12%  1%  9.1% 0 0 
[mpeg2video @ 0x7fdd6c4de9a0]00 motion_type at 33 26
[mpeg2video @ 0x7fdd6c4de9a0]Warning MVs not available
[mpeg2video @ 0x7fdd6c4de9a0]concealing 405 DC, 405 AC, 405 MV errors
[mpeg2video @ 0x7fdd6c4de9a0]00 motion_type at 26 28  1%  8.6% 0 0 
[mpeg2video @ 0x7fdd6c4de9a0]Warning MVs not available
[mpeg2video @ 0x7fdd6c4de9a0]concealing 225 DC, 225 AC, 225 MV errors
[mpeg2video @ 0x7fdd6c4de9a0]00 motion_type at 8 29%  1%  8.2% 0 0 
[mpeg2video @ 0x7fdd6c4de9a0]concealing 225 DC, 225 AC, 225 MV errors
[mpeg2video @ 0x7fdd6c4de9a0]skipped MB in I frame at 44 57.8% 0 0 
[mpeg2video @ 0x7fdd6c4de9a0]skipped MB in I frame at 41 10
[mpeg2video @ 0x7fdd6c4de9a0]skipped MB in I frame at 2 16
[mpeg2video @ 0x7fdd6c4de9a0]ac-tex damaged at 0 21
[mpeg2video @ 0x7fdd6c4de9a0]skipped MB in I frame at 2 26
[mpeg2video @ 0x7fdd6c4de9a0]invalid mb type in I Frame at 37 34
[mpeg2video @ 0x7fdd6c4de9a0]skipped MB in I frame at 1 11
[mpeg2video @ 0x7fdd6c4de9a0]skipped MB in I frame at 2 12
[mpeg2video @ 0x7fdd6c4de9a0]invalid mb type in I Frame at 0 13
[mpeg2video @ 0x7fdd6c4de9a0]invalid mb type in I Frame at 0 14
[mpeg2video @ 0x7fdd6c4de9a0]skipped MB in I frame at 1 15
[mpeg2video @ 0x7fdd6c4de9a0]invalid mb type in I Frame at 2 16
[mpeg2video @ 0x7fdd6c4de9a0]ac-tex damaged at 0 17
[mpeg2video @ 0x7fdd6c4de9a0]skipped MB in I frame at 1 18
[mpeg2video @ 0x7fdd6c4de9a0]invalid mb type in I Frame at 1 19
[mpeg2video @ 0x7fdd6c4de9a0]skipped MB in I frame at 1 20
[mpeg2video @ 0x7fdd6c4de9a0]ac-tex damaged at 1 21
[mpeg2video @ 0x7fdd6c4de9a0]skipped MB in I frame at 1 22
[mpeg2video @ 0x7fdd6c4de9a0]skipped MB in I frame at 2 23
[mpeg2video @ 0x7fdd6c4de9a0]ac-tex damaged at 0 24
[mpeg2video @ 0x7fdd6c4de9a0]invalid mb type in I Frame at 0 25
[mpeg2video @ 0x7fdd6c4de9a0]invalid mb type in I Frame at 0 26
[mpeg2video @ 0x7fdd6c4de9a0]invalid mb type in I Frame at 2 27
[mpeg2video @ 0x7fdd6c4de9a0]ac-tex damaged at 1 28
[mpeg2video @ 0x7fdd6c4de9a0]mb incr damaged
[mpeg2video @ 0x7fdd6c4de9a0]invalid mb type in I Frame at 0 30
[mpeg2video @ 0x7fdd6c4de9a0]invalid mb type in I Frame at 0 31
[mpeg2video @ 0x7fdd6c4de9a0]mb incr damaged
[mpeg2video @ 0x7fdd6c4de9a0]invalid mb type in I Frame at 0 33
[mpeg2video @ 0x7fdd6c4de9a0]skipped MB in I frame at 4 34
[mpeg2video @ 0x7fdd6c4de9a0]skipped MB in I frame at 1 35
[mpeg2video @ 0x7fdd6c4de9a0]concealing 1260 DC, 1260 AC, 1260 MV errors
[mpeg2video @ 0x7fdd6c4de9a0]ac-tex damaged at 35 10  1%  7.4% 0 0 
[mpeg2video @ 0x7fdd6c4de9a0]00 motion_type at 12 31
[mpeg2video @ 0x7fdd6c4de9a0]concealing 405 DC, 405 AC, 405 MV errors
[mpeg2video @ 0x7fdd6c4de9a0]mb incr damaged/ 24  9%  1%  6.7% 0 0 
[mpeg2video @ 0x7fdd6c4de9a0]00 motion_type at 24 29
[mpeg2video @ 0x7fdd6c4de9a0]concealing 810 DC, 810 AC, 810 MV errors
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code%  6.2% 0 0 
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]Missing picture start code
[mpeg2video @ 0x7fdd6c4de9a0]00 motion_type at 43 17  1%  6.0% 0 0 
[mpeg2video @ 0x7fdd6c4de9a0]concealing 270 DC, 270 AC, 270 MV errors
A:   0.6 V:   0.9 A-V: -0.253 ct: -0.004  28/ 28  9%  1%  5.7% 0 0 

Exiting... (End of file)
```

Is this some kind of piracy protection that is not allowing me my legally bought DVD??? Argh!

---

### Post by sandyvong on 2010-06-14
hii 

Ubuntu contains a number of DVD backup applications  (aka "DVD rippers").  To rip encrypted DVDs, you must install **libdvdcss2**  the same as you would to play encrypted DVDs (see [Playing  DVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")). 
There are several different  utilities targeted at ripping DVDs: 
 
**[SIZE=3][COLOR=DarkOliveGreen]_Thoggen (universe)_[/COLOR][/SIZE]**

 Rips DVDs and encodes them into Ogg files with Theora  video and Vorbis audio.  
 
**[SIZE=3][COLOR=DarkOliveGreen]AcidRip (multiverse)[/COLOR][/SIZE]**

 Rips DVDs and encodes them. 
 
**[SIZE=3][COLOR=DarkOliveGreen]k9copy (universe)[/COLOR][/SIZE]**

[k9copy]("https://help.ubuntu.com/community/K9Copy") is a Qt  based app that will make an exact copy of a DVD as an ISO file or as the  normal DVD folder structure on the destination drive. It can also  shrink and/or encode your DVDs to different formats such as AVI/MPEG-4,  MPEG-2, Flash Video (FLV), Real Video and QuickTime.

---

### Post by wilee-nilee on 2010-06-14
The restricted extras in synaptic. and
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by pmatos on 2010-06-14
> **wilee-nilee said:**
> The restricted extras in synaptic. and
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

For some reason after installing all Medibuntu stuff I still can't play it with mplayer but thoggen is able to encode it! :) Good! Thanks.

---

### Post by wilee-nilee on 2010-06-14
> **pmatos said:**
> For some reason after installing all Medibuntu stuff I still can't play it with mplayer but thoggen is able to encode it! :) Good! Thanks.

medibuntu provides the access to libdvdread, w32codecs and libdvdcss2, look for them in synaptic. I'm not sure but some of these may be part of the stock install, just look to see if they are installed, along with the ubuntu restricted extras. Also a excellent player with added codecs is vlc, I also use smplayer. The restricted extras would be xubuntu restricted extras or kubuntu restricted extras depending on the desktop your running, but they are basically cross compatible, but use the one for the desktop your using.

---


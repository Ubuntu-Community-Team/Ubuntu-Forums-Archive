---
title: "Can't get VCD's to work..."
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by pijiu on 2007-05-13
My CD/DVD-Drive does not detect any media when I try to play VCD's... I'm really stuck for ideas and would appreciate any help.

I'm also new to Ubuntu so if there's any specific info you need just ask and I'll try my best =)

---

### Post by madmetal on 2007-05-15
> **pijiu said:**
> My CD/DVD-Drive does not detect any media when I try to play VCD's... I'm really stuck for ideas and would appreciate any help.

I'm also new to Ubuntu so if there's any specific info you need just ask and I'll try my best =)

give a look here if you dont have codecs installed..
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
make sure you have installed multimedia codecs (follow site's instructions its easy..)
and if this wont work give a try with VLC player (search in synaptic)


UAResolved.

---

### Post by yapel on 2007-05-20
I have the same problem. I have done search/research in the forums. Loaded VLC and whatever others that have been mentioned, the good, the bad and the ugly, from the universe, multiverse, restricted, backports, whatsoever!  Managed to get DVD playing. But for VCD, no way!

BTW, I am running Ubuntu 7.04, x86-64 version on a AMD X2 based desktop computer.

---

### Post by Kingsley on 2007-05-20
Open up your terminal and type
```
mplayer -zoom vcd://2
```

You may need to replace vcd://2 with vcd:// or vcd://1

---

### Post by yapel on 2007-05-21
Well, I am working on VLC and Totem players. Guess this mplayer is another application which I have not installed yet.

Any hints for VLC and/or Totem please?

---

### Post by pijiu on 2007-05-21
I can get the VCD's now to play on mplayer, but they still won't mount. So basically I can't extract the data from the disc, which is what I really want to do with the VCD's.

---

### Post by yapel on 2007-05-21
Same here. My computer also cannot detect and mount VCD. No problem with DVD and AudioCD.

---

### Post by kwidzin on 2007-05-21
I switched to Arch. No problems with vcd. :D

---

### Post by yabbadabbadont on 2007-05-21
> **pijiu said:**
> I can get the VCD's now to play on mplayer, but they still won't mount. So basically I can't extract the data from the disc, which is what I really want to do with the VCD's.

You can't mount a VCD as they do not contain any filesystem.  (sort of the same way that audio cd's can't be mounted)  If you install vcdimager, you can use the tools it provides to rip the VCD.  (vcdxrip is the command you need to read about)

---

### Post by yapel on 2007-05-21
[QUOTE=yabbadabbadont;2695507]You can't mount a VCD as they do not contain any filesystem.  (sort of the same way that audio cd's can't be mounted)  [QUOTE]

My computer mounts AudioCD alright!

Could you elaborate what you mean by "VCD do not contain any filesystem" please? On ordinary Wintel PC, one can read the directory of VCD. Is this not some kind of "filesystem"?

---

### Post by yabbadabbadont on 2007-05-21
Apparently I was mistaken about not being able to mount VCDs.  However, it seems that they are created using a different mode than what is normally used on CDs (Mode2/XA or something like that).  Because of this, you need to use special software to extract the files from the disc correctly.  See here:
[http://www.mpegtv.com/faq.html#vcdtech](http://www.mpegtv.com/faq.html#vcdtech)

---

### Post by yapel on 2007-05-22
Thank you. The reference gives real good explanation. Am learning new things every day! ;)

---

### Post by swarup on 2007-06-04
> **Kingsley said:**
> Open up your terminal and type
```
mplayer -zoom vcd://2
```

You may need to replace vcd://2 with vcd:// or vcd://1

I am also having the same problem--my Ubuntu 7.04 does not recognize any VCD in the drive. It recognizes DVDs, but not VCDs.  I have Totem, Mplayer, and VLC, but none will even attempt to play a VCD because as far as the computer is concerned there is no media in the drive. 

I tried the above command, three times as per your instructions: once ending in "2", once ending in "1", and once ending in nothing (just vcd://). It opened the mPlayer screen when I used "2", but wouldn't play anything. With the other two options the Mplayer screen briefly flashed open and then closed. Here below is the terminal readout from each of the three tries. Can someone tell me what it all means, and what I should do to get VCDs playing. Thanks!
------------------------------------------------------------------------------------------------------------------

terminal printput from typing "mplayer -zoom vcd://2"

swarup@swarup-laptop:~$ mplayer -zoom vcd://2
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron A Mendocino/Pentium II Dixon (Family: 6, Model: 6, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing vcd://2.
track 01:  adr=1  ctrl=4  format=2  00:02:00  mode: 3
track 02:  adr=1  ctrl=4  format=2  00:18:67  mode: 3
track 03:  adr=1  ctrl=4  format=2  28:06:15  mode: 3
MPEG-PS file format detected.
VIDEO:  MPEG1  352x288  (aspect 8)  25.000 fps  1150.0 kbps (143.8 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 352 x 288 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 224.0 kbit/15.87% (ratio: 28000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 352 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.30:1 - prescaling to correct movie aspect.
VO: [xv] 352x288 => 376x288 Planar YV12  [zoom]
A:   0.7 V:   0.9 A-V: -0.150 ct:  0.022  15/ 15 168% 77% 44.4% 5 0 


----------------------------------------------------------------------
terminal printput from typing "mplayer -zoom vcd://"

swarup@swarup-laptop:~$ mplayer -zoom vcd://
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron A Mendocino/Pentium II Dixon (Family: 6, Model: 6, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing vcd://.
track 01:  adr=1  ctrl=4  format=2  00:02:00  mode: 3
track 02:  adr=1  ctrl=4  format=2  00:18:67  mode: 3
track 03:  adr=1  ctrl=4  format=2  28:06:15  mode: 3
libavformat file format detected.
LAVF_header: av_open_input_stream() failed
RAWDV file format detected.
VIDEO:  [DVSD]  720x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [dshow] DirectShow video codecs
Creating new registry
Decoder supports the following YUV formats: YUY2 UYVY 
Decoder is capable of YUV output (flags 0x9)
VDec: vo config request - 720 x 480 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 720x480 => 720x480 Packed YUY2  [zoom]
Selected video codec: [qdv] vfm: dshow (Sony Digital Video (DV))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libdv] Raw DV Audio Decoder
Unknown/missing audio format -> no sound
ADecoder init failed :(
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'dvaudio' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x56444152.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...
V:   0.0   0/  0 ??% ??% ??,?% 0 0 

Exiting... (End of file)

--------------------------------------------------------------------------------------------

terminal printout with typing "mplayer -zoom vcd://1"

swarup@swarup-laptop:~$ mplayer -zoom vcd://1
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron A Mendocino/Pentium II Dixon (Family: 6, Model: 6, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing vcd://1.
track 01:  adr=1  ctrl=4  format=2  00:02:00  mode: 3
track 02:  adr=1  ctrl=4  format=2  00:18:67  mode: 3
track 03:  adr=1  ctrl=4  format=2  28:06:15  mode: 3
libavformat file format detected.
LAVF_header: av_open_input_stream() failed
RAWDV file format detected.
VIDEO:  [DVSD]  720x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [dshow] DirectShow video codecs
Decoder supports the following YUV formats: YUY2 UYVY 
Decoder is capable of YUV output (flags 0x9)
VDec: vo config request - 720 x 480 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 720x480 => 720x480 Packed YUY2  [zoom]
Selected video codec: [qdv] vfm: dshow (Sony Digital Video (DV))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libdv] Raw DV Audio Decoder
Unknown/missing audio format -> no sound
ADecoder init failed :(
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'dvaudio' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x56444152.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...
V:   0.0   0/  0 ??% ??% ??,?% 0 0 

Exiting... (End of file)

---

### Post by scyleung on 2007-06-18
> **Kingsley said:**
> Open up your terminal and type
```
mplayer -zoom vcd://2
```

You may need to replace vcd://2 with vcd:// or vcd://1

The above code work for me, but you can't fast forward or something like that, which you can normally do it if you launch the mplayer thought the Application tap.:(

Is there any other way to do it?:KS

---

### Post by klytu on 2007-06-21
> **scyleung said:**
> The above code work for me, but you can't fast forward or something like that, which you can normally do it if you launch the mplayer thought the Application tap.:(

Is there any other way to do it?:KS

Yes. Try using the left and right arrow keys on your keyboard and the page up and page down keys. You can pause by hitting the space bar. Actually there are quite a lot of controls - those are just off the top of my head. See ```
man mplayer
``` for full info.

---

### Post by marx06 on 2007-06-26
I`ve had the same problem, this helped. Thanks Kingsley!

---


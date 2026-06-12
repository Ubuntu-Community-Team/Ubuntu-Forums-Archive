---
title: "mplayer mp3lib error under edgy"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by Jose Catre-Vandis on 2006-10-28
Just installed edgy, and after some configuration and Automatix 2 have a good working system. Only remaining issue at present is an error message generated when playing mpeg2 files with mplayer. I get the following message in a dialog box:
```
Requested audio codec family [mp3] (afm=mp3lib) not available. enable it at compilation
```

Now mplayer was installed through Automatix along with all the codecs, and i have tried a reinstallation through Synaptic but this message still comes up. The video plays OK, and with good sound. Here is the output if I request the video through the terminal:
```
mplayer 1strhood.mpeg
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) XP 1700+ (Family: 6, Model: 8, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
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

Playing 1strhood.mpeg.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  5750.8 kbps (718.9 kbyte/s)
==========================================================================
Requested audio codec family [mp3] (afm=mp3lib) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
Selected audio codec: [ffmp2] afm: ffmpeg (FFmpeg MPEG layer-1 and layer-2 audio decoder)
==========================================================================
Opening video filter: [pp=0x20077]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
[PP] Using external postprocessing filter, max q = 6.
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
[PP] Using external postprocessing filter, max q = 6.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 1024x576 Planar YV12 
alsa-uninit: pcm closed 0.014 ct:  0.062 101/101 19% 18%  2.5% 1 0 
```

Having just checked, I get the same error with any video or audio file I try to play.

Any suggestions on how to rid myself of this error or problem?

---

### Post by JohnLai on 2006-10-28
If you use GUI(gmplayer skin), go to Preferences, then click "codecs & demuxer". Select "FFmpeg....." for audio codec family. You may select ffmpeg for video codec family too!:KS

---

### Post by Jose Catre-Vandis on 2006-10-28
Thanks :) this gets rid of the error, but strange that under Dapper I do not need to select a codec choice. How will this affect any other files with different codecs, or encoding with mencoder?

---

### Post by cvmostert on 2006-11-11
> **Jose Catre-Vandis said:**
> Thanks :) this gets rid of the error, but strange that under Dapper I do not need to select a codec choice. How will this affect any other files with different codecs, or encoding with mencoder?

I had the same problem and also changed to ffmpmeg for audio and video...

then i got the error message:

ioctl dif1: Invalid argument

so i can choose which error i get :-) 

otherwhise the vcd seems to work fine (sound and video)

if there is a solution, i would be glad.

Thanks

---

### Post by tzulberti on 2006-11-15
Thanks, that solved my problem

---

### Post by partriv on 2006-11-16
AWESOME!  I just installed mplayer and was getting nothing but garbled audio output from it when I tried to play about 90% of the videos.  This fixed it!  Thanks :)

---

### Post by bsantos on 2006-11-17
For command line mplayer add the following to .mplayer/config

```
vfm = "ffmpeg"
afm = "ffmpeg"
```

---

### Post by dentaku65 on 2006-11-18
> **bsantos said:**
> For command line mplayer add the following to .mplayer/config

```
vfm = "ffmpeg"
afm = "ffmpeg"
```

Cool this fixed! 
:rolleyes:

---

### Post by Flash13 on 2006-11-20
> **JohnLai said:**
> If you use GUI(gmplayer skin), go to Preferences, then click "codecs & demuxer". Select "FFmpeg....." for audio codec family.

Worked fine, didn't need to set video aswell. :-D

---

### Post by StarQuake on 2007-01-10
Are there any negative side effects by doing this? Does it still select Quicktime or WMV codec if needed?

---

### Post by saygin on 2007-04-03
> **JohnLai said:**
> If you use GUI(gmplayer skin), go to Preferences, then click "codecs & demuxer". Select "FFmpeg....." for audio codec family. You may select ffmpeg for video codec family too!:KS

thanks a lot! It solved my problem. Thank you all! I love UBUNTU!

---

### Post by omac on 2007-04-24
Much thanks, solved it for me too.  :)

---


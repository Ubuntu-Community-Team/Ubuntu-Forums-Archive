---
title: "mplayer error AVC: nal size 0"
date: 2008-07-16
forum: Multimedia Software
---

### Post by steveyeager on 2008-07-16
I have a video clip from an Aiptek Action HD digital camcorder that plays back in MPlayer, but during playback it keeps displaying the error window Error! AVC: nal size 0.  The clip is a MOV file with h.264 compression.  It is not a perfect clip as it causes windows problems also, but it looks good and a previous distro I used played it wonderfully without the error.

Any thoughts?

---

### Post by shirilover on 2008-07-16
You can try passing the -really-quiet switch to MPlayer, that should at least get rid of that window.

---

### Post by steveyeager on 2008-07-16
Excellent.  That is exactly what I needed.  I suppose I need to find out what is wrong with the video and fix it.  But this is what I needed and why Ubuntu will always be one of the top distros available.  Thanks so much.

---

### Post by sken01 on 2008-11-07
how can i do that i don't undestand , i have the same problem.

---

### Post by sken01 on 2008-11-07
can you answer me about this error?  avc nal size 0

---

### Post by shirilover on 2008-11-08
The -really-quiet switch suppresses error dialogs.
It can be either added to a command line, like this
```

mplayer -really-quiet "video_file.ext"

```
or, it can be added to ~/.mplayer/config, like this
```

really-quiet=yes

```

As for the actual error, it seems to have something to do with h.264 video streams; but, I have been unable to find any explanatory data.

---

### Post by henryrhenryr on 2009-01-09
Hi

Thanks for the work around for the error messages.  I'm worried that the error still occurs.  When I launched mplayer from the command line:

gmplayer -really-quiet

and then ran a video (h.264 avc) I got the following output...  can anyone decode the output?  The video itself seems to play fine...

Thanks!

```
ISO: Unknown File Type Major Brand: avc1
Quicktime/MOV file format detected.
[mov] Video stream found, -vid 0
Warning! pts=1292288  length=1293312
MOV: durmap and chunkmap sample count differ (1262 vs 1263)
[mov] Audio stream found, -aid 1
VIDEO:  [avc1]  1280x720  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[h264 @ 0x89398d0]AVC: Consumed only 25 bytes instead of 28
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 236869 bytes instead of 236872
[h264 @ 0x89398d0]AVC: nal size 0
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
[ASPECT] Warning: No suitable new res found!
[h264 @ 0x89398d0]AVC: Consumed only 15225 bytes instead of 152280              
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 3317 bytes instead of 33209 0              
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 200029 bytes instead of 200032             
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 4077 bytes instead of 4080 18 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 15589 bytes instead of 155920 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 4669 bytes instead of 4672 24 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 4037 bytes instead of 4040 25 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 86393 bytes instead of 863966 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 6161 bytes instead of 6164 27 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 26349 bytes instead of 263522 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 10577 bytes instead of 105807 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 11229 bytes instead of 112320 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 43697 bytes instead of 437001 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 21377 bytes instead of 213806 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 22273 bytes instead of 222769 0            
[h264 @ 0x89398d0]AVC: nal size 0
A:   5.3 V:   1.7 A-V:  3.601 ct:  0.022  52/ 52 205% 19%  2.1% 50 0            

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

[h264 @ 0x89398d0]AVC: Consumed only 16253 bytes instead of 162561 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 9957 bytes instead of 9960 60 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 10073 bytes instead of 100764 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 7701 bytes instead of 7704 66 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 7713 bytes instead of 7716 67 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 7325 bytes instead of 7328 70 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 17989 bytes instead of 179924 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 5705 bytes instead of 5708 75 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 6441 bytes instead of 6444 79 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 5741 bytes instead of 5744 81 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 67745 bytes instead of 677486 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 2997 bytes instead of 3000 88 0            
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 24761 bytes instead of 247642 0            
[h264 @ 0x89398d0]AVC: nal size 0
A:   9.2 V:   3.1 A-V:  6.055 ct:  0.022  95/ 95 195% 13%  2.0% 93 0   
```

---


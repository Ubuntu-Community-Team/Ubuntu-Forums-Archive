---
title: "videoplayback of mp4 files is failing"
date: 2013-01-26
forum: Multimedia Software
---

### Post by byenary on 2013-01-26
Hi,
My 12.04 used to be able to play mp4 files, recently it stopped doing it properly, only showing a few frames, the sound continues adn now and then a frame appears but not playing video really..
It used to work before so I guess it has something to do with a recent update ?
Same behaviour in vlc,movieplayer,dragonplayer...
The resolution is rather high 1920x1080.
I downloaded a test mp4 file and plays fine but had smaller res.
But it worked before with my own vids, so...
Not sure where i need to start digging??
Thx

---

### Post by andrew.46 on 2013-01-26
Could you try your video from the commandline using MPlayer and post the terminal output here? If you have a supported card make sure you are using vdpau...

---

### Post by byenary on 2013-01-26
Well thanks, good idea,

The videos play flawless from commandline, the output states the system is to slow but this is condradictional information since its playing it perfectly :p
Great, now i'll have to explain my wife when she wants to watch a homevideo, she will have to use mplayer commandline <<:lolflag:](*,)](*,)
There must be a way to get this working again in vlc,

btw I upgraded to 12.10 but nogo... THANKS

---

### Post by byenary on 2013-01-26
note, the commandline had no playback
using a mplayer frontd like smplayer gives the same terrible result as vlc

---

### Post by andrew.46 on 2013-01-26
> **byenary said:**
> The videos play flawless from commandline, the output states the system is to slow but this is condradictional information since its playing it perfectly :p

Could you post the complete terminal output here? This will give more than a few hints as to what is going on.

---

### Post by byenary on 2013-01-27
Sorry I forgot, after updating vlc still stutters more then playing, movie player plays in slomo and command line mplayer also slomo.
Here the output, THX for your time/effort

byenary@byenary-ThinkPad-T60:~$ mplayer IMGA0146.MP4 
MPlayer svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing IMGA0146.MP4.
libavformat version 53.21.0 (external)
Mismatching header version 53.19.0
libavformat file format detected.
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0, -alang eng
VIDEO:  [H264]  1920x1080  24bpp  59.940 fps  17048.4 kbps (2081.1 kbyte/s)
Clip info:
 major_brand: mp42
 minor_version: 1
 compatible_brands: mp42avc1
 creation_time: 2012-12-25 17:52:33
Load subtitles in ./
Failed to open VDPAU backend libvdpau_r300.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 255.4 kbit/16.62% (ratio: 31920->192000)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 81
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1920x1080 => 1920x1080 Planar YV12 
A:   1.5 V:   0.9 A-V:  0.649 ct:  0.002   0/  0 138% 19% 16.7% 50 0 


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

A:  20.1 V:  12.4 A-V:  7.784 ct:  0.004   0/  0 125% 16% 23.7% 735 0 
No bind found for key 'CTRL-c'.
A:  27.5 V:  16.2 A-V: 11.350 ct:  0.002   0/  0 125% 16% 30.6% 965 0 


MPlayer interrupted by signal 2 in module: decode_audio
A:  27.8 V:  16.2 A-V: 11.522 ct:  0.002   0/  0 125% 16% 32.5% 967 0 

Exiting... (Quit)
byenary@byenary-T

---

### Post by andrew.46 on 2013-01-27
No hardware acceleration with vdpau, do you have an nvidia card?

---

### Post by byenary on 2013-01-27
hmm no it is a  Advanced Micro Devices [AMD] nee ATI Radeon Mobility X1400

---

### Post by andrew.46 on 2013-01-27
> **byenary said:**
> hmm no it is a  Advanced Micro Devices [AMD] nee ATI Radeon Mobility X1400

That is a pity as vdpau and a decent nvidia card can be the best way to play these big video files. Only option I can see is to resize the video although I know that in your first post you wrote that you used to be able to play these which is a little puzzling. Other than that I am not sure what to suggest I am afraid :(

---


---
title: "720p playback"
date: 2011-06-30
forum: Multimedia Software
---

### Post by the_obs on 2011-06-30
I have searched a lot for this, but couldn't get a clear, up-to-date, easy to understand solution to this problem.
I have a netbook with 2 gigs of ram, an Atom N280 (1.66GHz) under Ubuntu 11.04.
How can I play 720p MKV files? 

I was able to do it under XP with MPC and CoreAVC, but couldn't manage to port that solution to Ubuntu. I'm pretty much a beginner on Ubuntu and Linux, which is why I'm wondering if someone can give me a clear answer.

Thanks!

---

### Post by beew on 2011-06-30
Try using mplayer2 with gnome-mplayer as the front end.

Get mplayer2 from this ppa

[https://launchpad.net/~ed10vi86/+archive/tst]("https://launchpad.net/%7Eed10vi86/+archive/tst")


I am able to play a whole movie in 720 p (with many fast action scenes too) on a netbook with specs like yours with only the open source graphic card driver using this combination. Smplayer and Umplayer may work as front ends to mplayer2 in place of gnome-mplayer, but they use more resources (especially umplayer) so if you have a weak system I would say either use the command line (use mplayer without gui) or a simple gui like gnome-mplayer (very striped down)

---

### Post by the_obs on 2011-06-30
Thanks beew, that worked great! To be honest I wouldn't even know how to use the front-end (that's how nooby I am, is it simply a matter of installing gnome-mplayer?), but using the CLI is fine for now.
I tried viewing a heavy 720p MKV (~6.6 GB, no action scenes), and although I could view it, the video output was slowed down a bit (audio was fine, video wasn't choppy, just slow). It gave me the following output:

```
MPlayer2 UNKNOWN (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing GWH.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_DTS), -aid 0, -alang eng
[mkv] Will play video track 1.
Detected file format: Matroska
VIDEO:  [avc1]  1280x688  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Load subtitles in .
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[***] auto-open
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 2 threads if supported.
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [ffdca] afm: ffmpeg (FFmpeg DTS)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[h264 @ 0x1407e20]Cannot parallelize deblocking type 1, decoding such frames in sequential order
A:   0.0 V:   0.0 A-V:  0.000 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 
Movie-Aspect is 1.86:1 - prescaling to correct movie aspect.
VO: [xv] 1280x688 => 1280x688 Planar YV12 
A: 553.1 V: 551.9 A-V:  1.124 ct: -0.000   0/  0 126%  6% 16.7% 50 0 


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

A: 558.1 V: 555.5 A-V:  2.580 ct: -0.000   0/  0 121%  7% 15.7% 134 0 
  =====  PAUSE  =====
  =====  PAUSE  =====
  =====  PAUSE  =====

Exiting... (Quit)

```

Now is 6.6 GB just pushing it too much (or is size irrelevant?), or what can I do to optimize my system for viewing such files?

Thanks again chief!

---


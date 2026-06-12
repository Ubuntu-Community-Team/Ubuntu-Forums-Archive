---
title: "problem with 1080p with GeFroce 9600 GT"
date: 2009-11-07
forum: Multimedia Software
---

### Post by karoo on 2009-11-07
Hallo,
I have the following system setup:
CPU: model name    : AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
Graphic card: 02:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)

I have installed this driver from nvidia (not the OSS nv alternative): "185"

I am using ubuntu 9.10 64 bit. All my HDDs are encrypted, but I get transferrates around 25 mb/s so I don't think that the encryption is the problem.


HD-Movies with lower resolutions (720p) play without any problems.


If I play the movie with mplayer I get this alert message:
>           ************************************************
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

A: 129.1 V: 126.6 A-V:  2.498 ct: -0.001   0/  0 79%  3%  6.7% 1128 0 
Exiting... (Quit)

So is my System really too slow or is there any other possible reason those movies aren't working?
By the way I tried all the things mplayer is prosposing, but without any success

Here are some informations about the movie:
> [mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "X264", -vid 0
[mkv] Track ID 2: audio (A_DTS) "German DTS", -aid 0, -alang ger
[mkv] Track ID 3: audio (A_DTS) "Englisch DTS", -aid 1, -alang eng
[mkv] Track ID 4: subtitles (S_TEXT/UTF8) "German", -sid 0, -slang ger
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x800  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
[VO_XV] Could not grab port 280.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [libdca] DTS decoding with libdca
Stream with high frequencies VQ coding
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [dts] afm: libdca (DTS-libdca)
==========================================================================
I hope I gave you all the information you need to help me out of this mess :/

greetings
karoo

---

### Post by sc30317 on 2009-11-07
This should not be happening- that card is plenty good for 1080P

Have you tried playback on another OS?  Your hardware may be failing.

Also, try playing in VLC.

---

### Post by laceration on 2009-11-07
The video card is good enough...but you still are not really using the card, you are using the processor.  I have a cpu just a little better than yours, AMD x2 4400, so I know that they can play regular HD, but 1080 mkv is probably too much.
The good news is that the ver 180+ Nvidia drivers have vdpau which offloads video processing from the cpu to  the gpu(the chip on the video card) so you should be able to handle it, no problem.
Why it is not working for you is that you have to run a version of MPlayer with vdpau support and run it with the proper args or configuration.  I sorry I do not know if the current MPlayers have vdpau support, if they do not I'm sure you can find a ppa version with vdpau.  Do a search at [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

---


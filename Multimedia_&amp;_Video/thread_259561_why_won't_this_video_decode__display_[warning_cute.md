---
title: "why won't this video decode / display? [warning: cute overload]"
date: 2006-09-17
forum: Multimedia &amp; Video
---

### Post by ChrisC on 2006-09-17
My brother-in-law sent me some new videos of my 2-year-old niece, to be added to the little vanity site that I set up for her a couple months ago.  Thing is, I can't view them ... in MPlayer, Totem or VLC.  In all three cases, it either says it doesn't have the proper decoder, or it displays garbage.

This happened last month too (with the "Happy Birthday" video on the site), but I got around it using a Windows machine.  But today's videos won't even display on the Windows machine, using WinAmp, Window Media Player or QuickTime.

Can you take a look at this video file and tell me what's missing?  More likely, tell me what kind of encoding my brother-in-law is using that's causing all these systems to choke.  He's using Windows Movie to produce these, or whatever the free MS movie program is called.  I know, I know ...

[http://www.bridgetnewman.com/funny_sheep.mpg](http://www.bridgetnewman.com/funny_sheep.mpg)
(warning: approx 10 MB of toxic levels of cuteness)

I suspect that it's encoding in MPEG4 or 4:2:2 or something weird like that.

What's really weird is that it's displaying in the browser via plugin alright, or at least partially alright.  The browser is using mozplugger, which I believe means that it just uses whatever the system default is for that filetype.  I've tried all three standalone video players on my system (as inventoried above) and none of them work, so I'm not sure how the mozplugger method could be working, since as I understand it it just embeds the player.

---

### Post by ChrisC on 2006-09-17
Hmmm, it didn't include my sig, which is relevant:

---

### Post by jrib on 2006-09-17
It played on mplayer, vlc, and totem for me.  

If you are using totem-gstreamer I think the package you need would be gstreamer0.10-ffmpeg , but I would just install everything on [https://help.ubuntu.com/ubuntu/desktopguide/C/codecs.html](https://help.ubuntu.com/ubuntu/desktopguide/C/codecs.html) .  I'm not sure of the package that provides the decoding for the other video players, but I believe they should be installed if you used apt to install mplayer for example.  libmpeg2-4 *seems* to be the package that mplayer uses but this is most likely already installed....

As for the encoding information, mplayer -identify file, should give you tons of info.  Here is what I got:

```

(jasonr@luso:~/temp)% mplayer -identify funny_sheep.mpg                         (15:38)
MPlayer dev-CVS-060501-21:42-4.0.3 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron 4 Northwood; Pentium 4 EE/Xeon Prestonia,Gallatin (Family: 15, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.

Playing funny_sheep.mpg.
ID_VIDEO_ID=0
ID_AUDIO_ID=0
MPEG-PS file format detected.
VIDEO:  MPEG1  640x480  (aspect 8)  30.000 fps  2376.0 kbps (297.0 kbyte/s)
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
ID_FILENAME=funny_sheep.mpg
ID_DEMUXER=mpegps
ID_VIDEO_FORMAT=0x10000001
ID_VIDEO_BITRATE=2376000
ID_VIDEO_WIDTH=640
ID_VIDEO_HEIGHT=480
ID_VIDEO_FPS=30.000
ID_VIDEO_ASPECT=1.3333
ID_AUDIO_CODEC=mp3
ID_AUDIO_FORMAT=80
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=2
ID_LENGTH=34.41
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 640 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
ID_VIDEO_CODEC=mpeg12
alsa-init: using device default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 640x480 => 640x480 Planar YV12 
A:  22.8 V:  22.8 A-V: -0.011 ct:  0.047 669/669 15%  2%  2.2% 4 0 

```

and yes, very cute :)

[e] I am on edgy by the way in case versions of some packages are different for you

---

### Post by ChrisC on 2006-09-17
Thanks _jason.  libmpeg2-4 was already installed.  gstreamer0.10-ffmpeg wasn't installed, so I installed it (always using Synaptic of course) but that did not change anything -- video still garbled.  I don't want to try installing the packages identified in the URL you provided, since they are "bad"/"ugly" and I'm trying to keep this system as clean and stable as possible.

Thanks for the mplayer identify dump ... I don't see anything odd in there as far as video encoder, but I don't really have any experience in this.  Does anyone else see anything strange there, or can you point me to more solution ideas?  I have been using apt/Synaptic to install everything.

---

### Post by reclusivemonkey on 2006-09-17
> **ChrisC said:**
> Does anyone else see anything strange there, or can you point me to more solution ideas?  I have been using apt/Synaptic to install everything.

It works fine for me, but then I have "bad"/"ugly" installed...

---

### Post by Odinist on 2006-09-17
Awwwwww!!!!!!

---

### Post by ChrisC on 2006-09-17
Bump ... I really don't want to install something that has in *its filename* a warning that it's not ready for primetime ("bad"/"ugly").  I've got enough problems already ...

---

### Post by ChrisC on 2006-09-18
Well, I solved my problem.  But not the root problem ...

The stupid (literally) ftp program transferred the file in ASCII mode, not binary/image mode.

And know I know that apparently MPEG files survive an ASCII-mode transfer such that they will load in all MPEG players but the video and audio will be garbled.  The player does NOT simply reject the file!  I guess the headers survive but the elementary stream payload doesn't.

I use gFTP for ftp transfers, and from the first moment I've used it I have hated the fact that it doesn't have an "auto" setting for making obvious ASCII vs binary/image decisions.  And that's the root problem.  Grrrrrrrrr.

Thanks everyone!  And if you want more cuteness, check the root of that site late tonight when I'll have the rest of the videos up and thumbnailed and everything.  But mostly this is of interest only to my extended family :)

---


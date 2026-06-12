---
title: "mplayer subtitle problem"
date: 2009-12-06
forum: Multimedia Software
---

### Post by brandon88tube on 2009-12-06
For some reason I've been having an issue with some videos not displaying subtitles in mplayer. I've tried with and without A/SS enabled to no avail. I know the subtitles are there, but I'm totally lost as to why they won't show. Works fine with a ton of other videos. Is it trying to use a font I do not have? Any suggestions to get the subtitles working would be great.

---

### Post by lovinglinux on 2009-12-07
Have you tried [smplayer](apt:smplayer)?

---

### Post by brandon88tube on 2009-12-07
No offense, one I don't like smplayer and two, how would that help? Its just a gui frontend for mplayer.

---

### Post by lovinglinux on 2009-12-08
> **brandon88tube said:**
> No offense, one I don't like smplayer and two, how would that help? Its just a gui frontend for mplayer.

Because smplayer has a much better subtitle support than the default frontend.

---

### Post by rvm4000 on 2009-12-08
> **brandon88tube said:**
> For some reason I've been having an issue with some videos not displaying subtitles in mplayer. I've tried with and without A/SS enabled to no avail. I know the subtitles are there, but I'm totally lost as to why they won't show. Works fine with a ton of other videos. Is it trying to use a font I do not have? Any suggestions to get the subtitles working would be great.

It would be helpful if you post the command line you use and the output from mplayer.

---

### Post by brandon88tube on 2009-12-08
To lovinglinux, I don't use a front-end to mplayer. I use the no-gui version. To rvm4000, I just call up mplayer without any commands... well I've tried a couple dealing with subtitles and not a single one worked; I also have tried setting up a config file. I will however post the output. This is with a config file that has a/ss=yes and embeddedfonts=yes```
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/brandon/Downloads/white.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AAC), -aid 0, -alang und
[mkv] Track ID 3: subtitles (S_TEXT/***), -sid 0, -slang und
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  864x480  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
[***] auto-open
[***] Init
[***] Updating font cache.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 864 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.79:1 - prescaling to correct movie aspect.
VO: [xv] 864x480 => 864x484 Planar YV12 

```

---

### Post by rvm4000 on 2009-12-08
Have you tried to add the option **-sid 0**?

You could also try to press "v" during playback, just in case you have the visibility of subtitles disabled.

---

### Post by brandon88tube on 2009-12-08
> **rvm4000 said:**
> Have you tried to add the option **-sid 0**?

You could also try to press "v" during playback, just in case you have the visibility of subtitles disabled.

Tried it and didn't work. You really the developer of SMPlayer? If so, no offense with my above comment. Just don't like it.

---

### Post by lovinglinux on 2009-12-09
> **brandon88tube said:**
> To lovinglinux, I don't use a front-end to mplayer. I use the no-gui version.

Sorry, I didn't realize that.

---

### Post by x33a on 2009-12-09
are the subtitles working with other video players, vlc, totem, etc?

---

### Post by rvm4000 on 2009-12-09
> **brandon88tube said:**
> Tried it and didn't work.

I don't know, maybe there's something in those subtitles that mplayer doesn't like.

Is there any error or warning message in the output of mplayer when you use -sid 0?

> **brandon88tube said:**
> You really the developer of SMPlayer? If so, no offense with my above comment. Just don't like it.

Don't worry, not everyone has to like it ;)

---

### Post by brandon88tube on 2009-12-09
To lovinglinux, no problem its an easy mistake to make. Not many people opt for gui-less versions of apps.

To x33a, I have no idea... I don't have any of that installed. Working on a command line install that I updated to have have gui etc. So the apps I have are Terminal, Firefox, Pidgin, Transmission and that Sound Recorder app that came with some installed package. Oh and MPlayer, duh... Almost forgot that one. I would assume its fine as I haven't seen any comments about it from others. I have noticed that the subs I get for this one show tend to have an issue. Before I was able to get at least the subtitles to show up by turning off a/ss, but now that doesn't even work.

To rvm4000, here is the output of the -sid 0 option ```
brandon@koala:~$ mplayer -sid 0 ~/Downloads/white.mkv
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/brandon/Downloads/white.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AAC), -aid 0, -alang und
[mkv] Track ID 3: subtitles (S_TEXT/***), -sid 0, -slang und
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  864x480  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
[***] auto-open
[***] Init
[***] Updating font cache.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 864 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.79:1 - prescaling to correct movie aspect.
VO: [xv] 864x480 => 864x484 Planar YV12 
A:   2.7 V:   2.7 A-V:  0.000 ct:  0.023   0/  0 38%  3%  2.3% 4 0 
Exiting... (Quit)

```

---

### Post by brandon88tube on 2009-12-11
Nothing?

---

### Post by rvm4000 on 2009-12-11
The output of mplayer doesn't show any error about the subtitles... (maybe you can try to add **-v** to get more info)

What's the content of your ~/.mplayer/config? Maybe there's an option there preventing the subtitles to show.

Finally you can try to ask about this problem to the mplayer developers ([http://www.mplayerhq.hu/design7/mailing_lists.html](http://www.mplayerhq.hu/design7/mailing_lists.html)). They can help you better than anyone else.

---


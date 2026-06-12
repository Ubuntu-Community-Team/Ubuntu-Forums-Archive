---
title: "Having Troubles getting CoreAVC to work in Lucid  Lynx"
date: 2011-03-23
forum: Multimedia Software
---

### Post by penn919 on 2011-03-23
I know getting help for this might be a long-shot, but nonetheless here goes.

I've recently found out about a way to use Core AVC inside ubuntu and followed the following guides to get it up and running:

[http://code.google.com/p/coreavc-for-linux/wiki/DshowserverInstall](http://code.google.com/p/coreavc-for-linux/wiki/DshowserverInstall)

[http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation](http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation)

There were a few peculiarities during the installation process, but I personally thought I got it right based on the rough similarities between what was described in the step-by-step guide and what I was seeing on my screen, but I guess I must of gone wrong somewhere. Hopefully someone here can help me sort it out.

As of now whenever I attempt to play a video using this:

```
mplayer -vc coreserve /media/7E04971F0496D98B/striped/"Crysis 2 The Wall Trailer (1080p).mp4"
```

I get this:

```
Warning unknown option vo_driver at line 2
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/7E04971F0496D98B/striped/Crysis 2 The Wall Trailer (1080p).mp4.
libavformat file format detected.
[lavf] Audio stream found, -aid 0
[lavf] Video stream found, -vid 1
VIDEO:  [avc1]  1920x1080  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Forced video codec: coreserve
Cannot find codec matching selected -vo and video format 0x31637661.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A: 126.6 (02:06.5) of 126.9 (02:06.9)  2.1% 

Exiting... (End of file)
penn@ubuntu:~$
```

I was able to hear the audio, but I didn't get any video at all. The codec of the video file is  H.264 / AVC, so it should be supported by coreavc right? Any ideas on what I could've possibly done wrong?

I really hope I can get this resolved because it'd be great if I could successfully use my core avc license in ubuntu because WMP 12 seems to do just fine playing just about any HD video format in windows 7...definitely can't say the same about any player in linux, so hopefully this can work somehow.

---


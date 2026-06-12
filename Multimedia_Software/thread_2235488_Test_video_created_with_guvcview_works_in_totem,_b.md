---
title: "Test video created with guvcview works in totem, but fails in mplayer"
date: 2014-07-21
forum: Multimedia Software
---

### Post by syntaxerror74 on 2014-07-21
Hello there,

this problem is driving me insane, since I have no idea where to search for the bug.

I wanted to test my web cam (Logitech Communicate STX), and video capture worked fine, as did creating a test video with GUVCViewer. The latter program will create videos in MKV (Matroshka) container format.

Playing the test video in mplayer (VANILLA config, no changes from my side) shows a very bad sync and jittering picture, which will freeze soon after. I have a feeling that the codec is skyrocketing through the video (wrong speed).
Playing the test video in totem works perfectly.

I believe the culprit might be ffodivx, this is the video codec chosen by mplayer.

Full output:

```
andy@andy-lubuntubox:~$ mplayer guvcview_video-1.mkv
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing guvcview_video-1.mp4.
libavformat version 54.20.4 (external)
Mismatching header version 54.20.3
libavformat file format detected.
[lavf] stream 0: video (mpeg4), -vid 0
[lavf] stream 1: audio (mp2), -aid 0, -alang eng
VIDEO:  [MP4V]  320x240  0bpp   -nan fps    0.0 kbps ( 0.0 kbyte/s)
Load subtitles in ./
Failed to open VDPAU backend libvdpau_nouveau_vieux.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[VO_XV] Could not grab port 63.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 54.35.0 (external)
Unsupported AVPixelFormat 53
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Requested audio codec family [mpg123] (afm=mpg123) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, floatle, 160.0 kbit/5.67% (ratio: 20000->352800)
Selected audio codec: [ffmp2float] afm: ffmpeg (FFmpeg MPEG layer-1 and layer-2 audio)
==========================================================================
AO: [pulse] 44100Hz 2ch floatle (4 bytes per sample)
Starting playback...
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 320x240 => 320x240 Planar YV12 
A:   5.9 V:   5.8 A-V:  0.084 ct:   -nan   0/  0 ??% ??% ??,?% 0 0 

```

For a starter, something that definitely DOES look buggy here is the last line with the "-nan" (= not a number)!

---

### Post by syntaxerror74 on 2014-07-29
Any ideas, anyone?

---


---
title: "Only dragon player can play audio or video files"
date: 2008-08-25
forum: Multimedia Software
---

### Post by timcallagy on 2008-08-25
Hi Guys,

I've had this problem for a while now, and unfortunately not sure what I did at the time that might have caused it (possibly installed some codecs). I can't play video or audio files on Hardy with any media players except dragon player, the default KDE player. Dragon player opens all videos and audio files fine, but mplayer just shows a black window and totem stalls after 1 second.

Here's my output from mplayer:
################################################## #####################
$ mplayer 08\ Track\ 8.wma
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU T7250 @ 2.00GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags: MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 08 Track 8.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
================================================== ========================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16002->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
================================================== ========================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A: 1.5 (01.5) of 255.0 (04:15.0) ??,?%
################################################## #########################

From totem:
################################################## ########################
$ totem 08\ Track\ 8.wma
** (totem:1392): DEBUG: Init of Python module
** (totem:1392): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:1392): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:1392): DEBUG: Creating Python plugin instance
** (totem:1392): DEBUG: Finalizing Python plugin instance
################################################## ########################

From dragon:
################################################## ########################
$ /usr/lib/kde4/bin/dragon 08\ Track\ 8.wma
dragonplayer(1166) Phonon::KdePlatformPlugin::createBackend: using backend: "Xine"
################################################## #######################

Anybody have any ideas or suggestions?

Thanks in advance,

Tim

---


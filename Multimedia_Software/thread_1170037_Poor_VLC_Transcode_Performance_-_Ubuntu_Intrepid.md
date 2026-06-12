---
title: "Poor VLC Transcode Performance - Ubuntu Intrepid"
date: 2009-05-25
forum: Multimedia Software
---

### Post by domoso on 2009-05-25
Hey all. I originally posted on the videolan forum but, I've yet to receive any suggestion for my problem. I'm attempting to get VLC setup for transcoding captured video from my TV tuner. I originally had this working flawlessly when I ran Windows XP with playlists for channel changing. It was great! However, I've since switched over to Ubuntu 8.10 (all desktop visual effects are disabled) and am attempting to duplicate my Windows setup. I've run into several problems. The most significant issue is performance. So far, I'm only attempting to transcode existing Xvid video files. I haven't even attempted to transcode live video from my TV Tuner yet. Whether I attempt to transcode Video and Audio or Video only my CPU utilization is excessive.

My hardware (same as it was under Windows XP):
AMD Athlon XP 2500+
2GB RAM
NVidia Geforce 6600

Transcode settings:

Video: DIVX3 256Kb/s (same as it was under Windows XP)
Audio: Vorbis 96Kb/s (NOT the same as Windows XP, I can't seem to find the correct files to install for MP3 encoding. I encoded MP3 under Windows )

I'm getting a bunch of this:

[00000525] avcodec encoder warning: rc buffer underflow
(msmpeg4@0xa366da0)
[00000509] stream_out_transcode stream out debug: late picture skipped (4631)
[00000515] main mux warning: late buffer for mux input (164881)

This is resulting in dropped frames. My CPU usage is tapping out at ~90% +/-. Under Windows it would hover around 60 - 70% when transcoding live video from my TV Tuner and everything was flawless.

Everyone I talk to says Linux is more efficient than Windows. Yet, I'm not exactly seeing that in practical applications. Perhaps I'm doing something incorrectly. I don't know. Any assistance is appreciated.

---


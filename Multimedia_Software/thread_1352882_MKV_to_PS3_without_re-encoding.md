---
title: "MKV to PS3 without re-encoding"
date: 2009-12-12
forum: Multimedia Software
---

### Post by Emanuele_Z on 2009-12-12
Hi all,

I'm trying to find a solution to extract h.264 video (and audio) from a MKV container and insert those sources in an mp4/m4v container that PS3 is able to playback.
Now, I don't want to re-encode the video, as seen as the video format is already h.264 encoded; maybe the audio should be converted from DTS to AAC.

Avidemux should be the ideal candidate but unluckily it crashes, MKV support is flaky (sometimes it pops strange errors, some other times it badly re-encodes audio... ) and audio conversion (DTS --> AAC) is a bit bugged as well (when it doesn't crash it goes out of sync).

I could use HandBrake, but that program will force a video re-encode as well (MKV video source is already well done with h.264) and I don't want to do it for 2 reasons: the quality will be worse and it'll require 5x time (eg 10 hrs for a 2 hrs MKV file).

At the end of the day it's just:
[list]
[*] opening the MKV container
[*] extract Video and Audio track(s)
[*] (optional) re-encode the Audio to AAC
[*] put together Video and Audio in a PS3 compatible mp4 (in case split if file is bigger than 4GB)
[/list]

I managed to get a script form this forum, fixed some bugs in it, but the problem is that when I have to re-econde the audio from WAV to AAC and the file is > 4gb **neroAacEnc** fails (it uses the *small* C file api - like *fopen* instead of *fopen64* - max 4GB) while if I use **faac** it will go out of limits (when reaching the 100% of file processed it will go out of boundaries indefinitely)...

I was forced to use VirtualBox with Windows XP and the software mkv2vob (naturally turning off video re-encoding).
Apart that it took ages, it worked.
Still it's not a viable solution because it takes too long and consumes too many resources (disk spin too much because of virtual memory).
But I've seen that mkv2vob uses **mencoder** (the encoder version of mplayer).
Is it possible to use it to convert from WAV (and or DTS) to AAC?
If yes I could try that route...

Anyone can help?

Cheers,

---


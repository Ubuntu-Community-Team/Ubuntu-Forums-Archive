---
title: "Strange audio stutter problem with Mplayer"
date: 2008-09-15
forum: Multimedia Software
---

### Post by diobrando on 2008-09-15
Hopefully someone can shed some light on this issue for me. I'm having a strange audio stutter issue which only happens with certain files. I know it's not an issue with the file as it plays fine in VLC, and also plays fine with mplayer on another computer.

First up, some background. 99% of my video files play perfectly fine in Mplayer. I'm using the AMD64 version of hardy heron. Due to an issue with video playback on my video card (ATI Radeon HD4850) I couldn't use the Mplayer in the repositories, I had to patch the source and compile it myself. The problem is with a few files all encoded the same way. FFMpeg tells me:

> 
Duration: 00:24:49.8, start: 0.000000, bitrate: 1284 kb/s
  Stream #0.0(und): Video: h264, yuv420p, 960x540, 23.98 fps(r)
  Stream #0.1(eng): Audio: mp2, 48000 Hz, stereo


During playback, always at the exact same times, the audio skips and repeats itself/stutters. The audio playback speed also seems to fluctuate, like it is speeding up for a few seconds and then going back to normal. If I run mplayer with -ao null (no video output) I have the same issue. There appears to be no issue with the video playback. These files are all in .mp4 container format. I've tried playing around with the -autosync option and had no luck with that. I'm not really sure where to go from here, so any help or suggestions to try would be appreciated.

---

### Post by diobrando on 2008-09-16
bump

---

### Post by diobrando on 2008-09-23
After messing around with it a bit more it appears that this problem is limited to mp2 audio tracks, everything else works fine.

Any help, please?

---

### Post by markbuntu on 2008-09-23
Which plugin are you using for the audio?

---

### Post by lovinglinux on 2008-11-18
I'm experiencing the same problem with mp4 videos with audio encoded as mp2.

If I extract the audio from the mp4 file, using Avidemux, re-encoding it to mp3 or ac3, then muxing it back with the video into a mkv file, using mkvtoolnix, it plays fine. Unfortunately, a few videos become glitchy at certain points. Other videos are perfect.

I would appreciate if someone could provide a better alternative, specially one that do not involve extracting, encoding and muxing the streams.

---


---
title: "[SOLVED] mplayer hi def : audio sync"
date: 2008-02-07
forum: Multimedia &amp; Video
---

### Post by uncannybuzzard on 2008-02-07
i'm trying to play an avi at 720p using mplayer. i'm using gl playback and sdl for audio. the video is not choppy at all, however it's slow enough the the audio continues to get more and more out of sync. i've tried frameskipping and the results are not watchable. it does this with matroska videos as well. i've heard this is a known issue, but can't find much on it. i'm running mythtv on a P4 2.4 with a nvidia fx5200 card (which should work in theory). any ideas?

---

### Post by jan quark on 2008-02-08
have you tried another player? like vlc.

I know it is not a solution click that and everything is fine, but perhaps it is a mplayer related issue and we are going to spent many hours fixing it to no avail. perhaps other players will just work

---

### Post by falstaff on 2008-02-08
You have two possiblities to solve this problem:

1. Use a hardware Audio decoder (if you have AC3/DTS audio streams)
2. Use CoreAVC, a _very_ fast H.264/MPEG4 AVC decoder... (see here [http://code.google.com/p/coreavc-for-linux/](http://code.google.com/p/coreavc-for-linux/))

bye
falstaff

---

### Post by uncannybuzzard on 2008-02-10
ok, i somewhat solved this. this is what's working for me

```
#!/bin/bash

mplayer -monitoraspect 16:9 -fs -zoom -quiet -lavdopts fast=1:skiploopfilter=all -ni -vo gl "$1"

```


i've heard that XV is the output best suited for HD but i've had much better results with gl
this gets 720p working for most of the movies i've downloaded. i haven't tried 1080, but 720 puts about a 70% load on the CPU

---


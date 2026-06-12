---
title: "SMplayer and fglrx"
date: 2011-04-23
forum: Multimedia Software
---

### Post by nishant.singh28 on 2011-04-23
I've been using SMPlayer for ages, and was fairly satisfied with it, except for the fact that the videos looked a bit faded with the AVIVO xv driver. Then I switched to gl(fast ATI cards), and the colors improved, but it was nearly impossible to watch a video without going in to fullscreen. Once in fullscreen, I had no access to the right-click menu, the control bar, nor could I alt-tab out. I have tried a lot of different video drivers, but I can only use gl or gl2, and both have this problem.
The problem exactly is that the videoo flickers badly when not in fullscreen, and even if it is not in focus, I can still see the video flickering over everything else. aLso, lately it has no sound when I open a file I have opened before till I switch to fullscreen. Once I go to fullscreen, it has audio even if I come out of full mode into windowed. But there is no audio till it first goes into fullscreen.
Now the version of SMPlayer is from the repos, but MPlayer is from a PPA, because the repo version can't play some avi files in fullscreen. The graphics issue is common to both versions, I don't know about the audio issue if it exists in the repo version as well.
Hardware:
```
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
```
fglrxinfo:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4500 Series
OpenGL version string: 1.4 (3.3.10237 Compatibility Profile Context)
```
Ubuntu 10.10 x64 with fglrx 8.780

Log files of both smplayer and mplayer while opening a file attached.


EDIT: Another detail I forgot to give was that this issue is most apparent in files with h264 encoding.

---


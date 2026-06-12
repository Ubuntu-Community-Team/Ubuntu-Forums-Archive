---
title: "GOPchop either crashes or has transparent video on 64-bit"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by deruberhanyok on 2007-10-28
So I wanted to try using GOPchop to manually cut commercials from some TV shows I recorded. I'm running 64-bit gutsy with the nvidia 'new' drivers from the repository. Also, I have the desktop effects enabled.

I'm running into two problems. The first is that when using 'xv' or 'xv2' video output the program quits as soon as it finishes loading a file. X11 output solves this and it only rarely quits after loading. This leads me to the second problem: when using the 'X11' video output the video display is so transparent I can only barely see the video.

I've tried various setting for window opacity in ccsm to no effect. Also, I've run VLC using both xv and x11 output and verified they both work fine on my system.

Does anyone have any suggestions as to what I could try to resolve either (or both) of these issues?

[edit] Well, the X11 output is fine (I can see it) if I disable the desktop effects, but the program still crashes when trying either of the xv outputs. Also, I've found that with effects enabled and using X11 output the program will crash on load unless I go to preferences, change the output type to xv, save, go back to preferences and change the output back to X11.

---


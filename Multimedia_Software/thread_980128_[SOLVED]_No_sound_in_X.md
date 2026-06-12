---
title: "[SOLVED] No sound in X"
date: 2008-11-12
forum: Multimedia Software
---

### Post by SteinbergerNate on 2008-11-12
Sound had been working in xfce but today I noticed that it hasn't been working when I went to watch a you tube video. Looked at the corner and the volume applet showed that the volume was all the way down so I clicked it up and it went right back down to nothing.

So, I opened up the volume program and there aren't any sliders. Went to options and it doesn't give me any options on what sliders to show. The only device listed is "default"

I ran aplay -l and it tells me there are no sound cards. When I run it at the terminal before I start X, it shows me my audio devices. If I try to play anything with audio from mplayer in X then it says that it can't initialize the audio device. When I play an mp3 from the terminal before I start X with mplayer, it plays just fine.

What setting am I missing in xfce (or xorg for that matter) that has cause my sound to stop working?

---

### Post by SteinbergerNate on 2008-11-12
Never mind. I figured it out. Somehow, I got removed from the audio group. Edited /etc/group and added my username to the audio line and it works fine. Don't know why it worked outside of X though.

---


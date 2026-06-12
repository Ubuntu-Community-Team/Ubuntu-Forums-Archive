---
title: "[SOLVED] Rhythmbox not playing so low bass"
date: 2008-12-11
forum: Multimedia Software
---

### Post by magnus0 on 2008-12-11
If I play a song, that has some really low bass effects, like Korn - Dead Bodies Everywhere beginning (Test it yourself: [http://www.fileden.com/files/2006/9/28/244597/Korn - Dead Bodies Everywhere.mp3](http://www.fileden.com/files/2006/9/28/244597/Korn - Dead Bodies Everywhere.mp3)), the bass gets sloppy at the end of the beat. If I play it in Banshee, it plays fine. They both use Gstreamer, so what could be wrong? I'm also using Gstreamer equalizer. This happens with and without it.

---

### Post by magnus0 on 2008-12-16
I found the problem. I was using the crossfade backend in preferences. Turned that off, everything was fine.

---


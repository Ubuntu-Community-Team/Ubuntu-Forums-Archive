---
title: "Real Player 11 (Gold) Sound Problem"
date: 2009-10-26
forum: Multimedia Software
---

### Post by Normalex on 2009-10-26
Real Player 11 (Gold) deb package from Real.com directly uses Alsa sound card which in turn prevents other programs to output any sound. And vice versa, if other program started output before Realplayer, then it will start without any sound support.

To resolve this behavior go to Tools->Preferences->Hardware tab. In the "PCM Device:" field enter "default". Click OK and restart Realplayer.

Cheers.

---


---
title: "No center/LFE, other channels work, 10.04, X-Fi"
date: 2010-04-29
forum: Multimedia Software
---

### Post by Vectorferret on 2010-04-29
X-Fi Fatal1ty Extreme Gamer
It doesn't matter if I set the audio to 5.1 or 7.1, the center and LFE are silent. I had the same problem in 9.10 but I could work around by using the alsamixer to set the center to 90%, quit, then set back to 100%. This doesn't work in 10.04 as the controls in the alsamixer can't be changed. Is there any way I can get the center channel working? All I can do at the moment is set the sound properties to 4.0 so that the center channel is automatically redistributed to the other channels, but that isn't a great solution.

---

### Post by Vectorferret on 2010-04-29
Solved this on my own. alsamixer started working again after a reboot, and it properly displayed the center/lfe as muted, so I unmuted it and everything worked. I have no idea what went wrong, but the problem was with alsamixer incorrectly displaying, not the audio itself.

---


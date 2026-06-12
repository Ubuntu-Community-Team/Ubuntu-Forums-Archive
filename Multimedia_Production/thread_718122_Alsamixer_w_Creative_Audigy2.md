---
title: "Alsamixer w/ Creative Audigy2"
date: 2008-03-07
forum: Multimedia Production
---

### Post by Bobby55 on 2008-03-07
Noob Q about recording via alsamixer: I'm running my gear into a small Behringer mixer, using the CD out from the mixer into Line2 on the Live!, running the headphones out on the Live! back to the CD in on the mixer.  Anyone have stable consistent settings for alsamixer getting recording to work during playback?  I've set the Playback -> Wave and Aux2 to 90%, Recording via Line2.  It's really inconsistent.  This is really driving me nuts!  TIA for any help.

---

### Post by Bobby55 on 2008-03-09
Found it!  I assumed JACK was handling the routing automatically.  It wasn't, I had to manually route each recorded new track to the ALSA playback device to hear it again:guitar:.

---


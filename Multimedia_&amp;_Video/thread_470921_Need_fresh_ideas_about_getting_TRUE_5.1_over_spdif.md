---
title: "Need fresh ideas about getting TRUE 5.1 over spdif (via 82xx alsa driver)"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by cbockenhouser on 2007-06-11
Here's the scenario: Mplayer plays movies beautifully and turning on the ac3 passthru causes my receiver to recognize a real 3/2 DTS signal.  The problem is that the signal is still being downmixed somewhere  so it only uses the front left/right speakers (3 of 5 channels produce nothing).  I've tried several mkvs all encoded with real 5.1 audio, same results.

Since the software can set the correct mode on the receiver it seems like the only thing I need to do is disable whatever is downmixing the source signal.  Seems like it might be an alsa bug....

any ideas?

(i respectfully ask that you not refer me to any other guides or posts that don't specifically address this issue with this soundcard because I'm quite certain I've seen and attempted them all with no success.)

p.s. its definitely a downmix happening because the center channel (voice) tracks are clearly audible on my front left/right.

---

### Post by cbockenhouser on 2007-06-12
does anyone have 5.1 over spdif working on a via8237 ??

---

### Post by rider2112 on 2007-12-12
I have the exact same problem on my machine with the same sound card.... It's driving me up a wall!  When i play something with 5.1 sound over SPDIF, i only get FL and FR (front left and right).  No center (so no dialog durring movies) and no rear speakers or LFE.  

The strange thing is that the sound card is outputing 5.1 in analog (it remaps the line in / mic in to be Center / LFE  and Rear channels)....  Unfortunately, my receiver doesn't have 5.1 analog input, only stereo.

I've tried every setting under the sun... done "sound-test -Dplug:surround51 -c6 -twav (my syntax might be garbled, im writing this from memory"  but all i get is FL and FR over SPDIF... 


One other strange thing.  In ubuntu's volume control, when i have "IEC958 Playback AC97-SPSA" muted, i get audio over SPDIF through the FL and FR speakers...  As i adjust the level of the "IEC958 Playback AC97-SPSA", i get audio intended for the Center, RR, RL and LFE, however it play's through the front left and right speakers speakers.

cbockenhouser - what receiver are you using?

---


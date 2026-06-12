---
title: "System freezes while video playback under Compiz"
date: 2009-11-07
forum: Multimedia Software
---

### Post by Nat90 on 2009-11-07
Hello everyone;

Here's the thing, using jaunty 9.04(64-bit), 1Gb of Ram, and 2 Gb of Swap I used to be able to watch movies on full screen under Compiz with VLC player with no problems, however, video playback did get stuck with SmPlayer and other players (every 10 minutes or so, the video stops for a few seconds while the audio continues, and the whole system freezes). I think this happened because VLC uses it's own engine.

After I upgraded to Karmic 9.10(64-bit), this problem started occurring with VLC player as well (and every other player), which is now, version 1.0.2, I think before it was 0.9.8
So, I went out and bought me another 1Gb of Ram memory. But after I installed it, and reinstalled Ubuntu, widening the Swap memory to 4Gb, the problem  persisted. Now I'm constantly changing between Compiz and Metacity with 'fusion-icon' which I find excruciating because I would like to enjoy Compiz to it's full.

To add info: My processor is an AMD Athlon 64 X2 Dual Core 4200+
And my graphics card is a Nvidia 6150, integrated to the Motherboard. Also as I already said, I have 2Gb of Ram, and 4 Gb of Swap.

Shouldn't this be enough to run Compiz smoothly? Or is there something I can do to fix this?

Thank you for the help.

---

### Post by rvm4000 on 2009-11-07
Some people report similar problems. I don't know if it's your case, but if you have those players configured to use alsa as audio driver, try to change it to pulse.

---


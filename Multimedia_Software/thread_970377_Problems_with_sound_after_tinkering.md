---
title: "Problems with sound after tinkering"
date: 2008-11-04
forum: Multimedia Software
---

### Post by psz21 on 2008-11-04
Hi,

I somehow managed to screw up my sound settings by doing the following:

I installed iTunes 7.5 under wine. It went OK with smaller problems, and iTunes worked. But as it was painfully slow, I decided to remove it. I tried it with wine/uninstall, but it didn't work. After trying a few times, I decided to remove wine completely. Up to this point sound was fine.
After removing wine, my sound went crazy. In system/preferences/sound I manage to get a test sound (white noise), but there is no sound for live web streams, or embedded media. VLC doesn't have any sound either. With Rhythmbox, I manage to get sound when playing mp3s, but that's 99% noise, and 1% music. However, when playing DVDs under mPlayer, the sound is perfect. Before my tinkering, sound was fine with all the mentioned applications.

I tried removing ALSA (with --purge) and reinstalling it, but there was no change.

Prior to all of this, I also wanted to get my microphone to work, so I installed Pulseaudio, but that had no effect on the sound coming out of the computer (neither on my mic, but that's another question). I also tried removing then reinstalling Pulseaudio, but the problem remains.

Any suggestions to solve the problem without the need to completely reinstall Ubuntu?

BTW, I'm using Ubuntu 8.04 (with latest updates).

Thanks!

---


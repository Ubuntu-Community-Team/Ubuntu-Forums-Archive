---
title: "Switched from Gentoo to Ubuntu now mythtv has some problems with sound"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by Saubazi on 2007-07-10
I got the idea of switching from Gentoo to Ubuntu on my Media-PC. Everything is fine sofar it was quite easy to get the PC up and running again, however, I am having problem with the passthrough sound to SPDIF.

I downloaded a sample file with dolby digital and I can play it with aplay -D surround51 or with aplay -D hw=0,1 and I get full surround sound via SPDIF. I am also able to play it with xine but I am stuck with mplayer.  For example, mplayer -ao alsa:device=surround51 will just bring a scratchy noise.

This is just as a background - my main problem is the passthrough of digital TV sound. I had this running in Gentoo so that broadcastings with DVB-T were full surround. Now I get only stereo. The funny part is that
I have set audio output as /dev/dsp and passthrough device as alsa:device=surround51 and activated AC3 passthrough checkbox.

I can play a DVD and I get proper passthrough but with DVB-T it's nogo :( - I am in a bit of a loss with this issue...

---


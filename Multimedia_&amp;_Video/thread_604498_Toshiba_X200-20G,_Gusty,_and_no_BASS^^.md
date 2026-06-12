---
title: "Toshiba X200-20G, Gusty, and no BASS^^"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by xav1664 on 2007-11-06
Hi ,

I have a sound issue on my toshiba X200-20G, running perfectly on Gusty. The sound works, but only on the tweeters and mediums, not on the bass one...:confused:

globally the sound quality is not fantastic, i had install the alsa-driver-1.0.15rc1...i don't feel any difference in quality of sound and the bass speaker still doesn't works.

The only improvement i have eared is when i play some music with XMMS player, the sound quality is really better (for me no difference when played under vi$ta, only still the bass speaker).

this solution doesn't works too: 
sudo aptitude install linux-backports-modules
and add the option in the file /etc/modprobe.d/alsa-base :
options snd-hda-intel model=toshiba


So if there is anyone who can make jump is laptop on each bass wave, give me your tips xD...thank you in advance:)

---


---
title: "tried to update alsa drivers, broke sound (hda intel)"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by riahmatic on 2007-12-30
Edit: Sound is back... mysteriously.

I'm using Gutsy on my Dell Inspiron 1420 laptop, and sound was previously working but sometimes not after resuming from suspend. So, I used the guide on how to compile your own alsa drivers ([https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)) with the latest alsa packages (1.0.15) and everything seemingly compiled and installed correctly. But then no sound was coming out at all after rebooting. I tried adding "options snd-hda-intel model=3stack" and rebooting, but still no sound. I tried media files, the sound preferences, but still no sound through laptop speakers or headphones. It doesn't throw any errors or give indication that it shouldn't work and I've made sure all levels in the mixer aren't muted.

So then I tried to revert back to where I was at originally, running "sudo make clean" on everything I just compiled, but that didn't bring sound back.

I've done a lot of searching, but... still not sure how to debug this.

---


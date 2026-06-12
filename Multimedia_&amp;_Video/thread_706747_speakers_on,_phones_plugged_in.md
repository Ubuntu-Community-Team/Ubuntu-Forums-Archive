---
title: "speakers on, phones plugged in"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by andradx on 2008-02-24
Everytime I plug in my phones sound keeps coming out of the speakers. I tried reading as many threads about this issue as possible and still couldn't get it right.

There were lots of answers about using the alsa mixer and the volume control of the different slots(?). Thing is whenever I mute the headphone slider speakers sound is also muted, and if I slide down to mute PCM or Front the same thing happens with the headphones sound. 

(I am not sure if the speakers play simultaneously with the phones on or no when I first installed Ubuntu. At that time while using good Koss headphones with proper sound isolation I never noticed it but on not so isolated ipod phones I did, so I wouldn't know if it could be due to any program I installed later and they were lots, trying to play .aac and getting ipod interface):confused:

OK, just for the record and for anyone interested.
I typed into the terminal **cat /proc/asound/card0/codec#* | grep Codec** to see the soundcard codec.
Then I searched for its options in [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt#19]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt#19") under snd-hda-intel section and no LG model or similar whatsoever was listed.
So I tried a bit of brute force and ended up by selecting 3stack-hp which enables in the alsa-mixer a ticker for turning the headphones on and off. So much for the automatic switching between the speakers and headphones whenever a jack is plugged in.

I don't know about its dependencies but linux-backport-modules and also the alsa-driver/utils/lib are up to date.

---


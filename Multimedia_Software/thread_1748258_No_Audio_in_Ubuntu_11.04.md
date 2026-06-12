---
title: "No Audio in Ubuntu 11.04"
date: 2011-05-03
forum: Multimedia Software
---

### Post by khurramjavaid94 on 2011-05-03
I just installed Ubuntu 11.04 as dual boot with windows 7. But no sound on my Creative Audigy 2. Its working fine in Windows 7. I have already disabled the built-in sound card from Bios, searched for drivers, played with audio settings, still no luck.
So what can be the problem.

I am using 5.1 audio system.

---

### Post by leeishom on 2011-05-04
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

and then....

sudo apt-get install linux-sound-base alsa-base alsa-utils


Worked for me, using an intel chip.

---

### Post by lidex on 2011-05-04
If your Creative Audigy card is not giving you any sound, make sure the analog/digital check box in your sound mixer is unchecked. Updates seem to reset this switch regularly so keep this in mind.

---

### Post by Elevon on 2011-05-05
> **lidex said:**
> If your Creative Audigy card is not giving you any sound, make sure the analog/digital check box in your sound mixer is unchecked. Updates seem to reset this switch regularly so keep this in mind.

I had a problem with 64 bit version of Ubuntu 11.04 and Audigy 4 sound,it was coming out very low and distorted for anolgue 5.1 sound ,fix was download and install GNOME Alsa Mixer then make sure you put a tick in the analog/digital box,which fixed my problem :).

---

### Post by bpayne71 on 2011-05-19
Thank you Elevon...I was having the same issue with my Creative card in 11.04 and I could not get it to work.  I read your post about d/ling the Alsa mixer and I did and it resolved my problem.  Again thank you...I am a full fledged user of Linux now.

---


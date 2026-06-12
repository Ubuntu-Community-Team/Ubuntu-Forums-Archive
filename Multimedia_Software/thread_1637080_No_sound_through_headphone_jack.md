---
title: "No sound through headphone jack"
date: 2010-12-04
forum: Multimedia Software
---

### Post by locksalordy on 2010-12-04
Hi,

Apologies for posting a new thread for what appears to be a common issue, but I have followed all other similar threads with no solution.

I have a Dell Vostro 320 running Ubuntu 10.10. I can get sound through the onboard speakers but when I plug headphones into the jack, the onboard speakers mute (correct behaviour), but no sound comes from the headphones (incorrect behaviour). The headphones do work with other sound sources.

I have made sure all the alsa drivers are up to date and correct and the system is seeing the sound card OK according to aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The alsamixer run from the command line or Gnome shows "Master", "PCM", "Beep" and "Capture" all normal with nothing muted. The alsa-base.conf file has the following as the last line as per various posts that seem to have a fix for this problem:

options snd-hda-intel model=dell-vostro position_fix=0 enable=yes

I am tearing my hair out which is not a good idea seeing as how I don't have much to loose. Hope someone can help.

Thanks,

locksalordy

---

### Post by locksalordy on 2010-12-04
Hello Again,

Joy! After trying a full power down, the system came up with the sound card working as it ought.

Apologies for posting before doing this.

locksalordy

---

### Post by carl lindsay on 2010-12-04
i am using an apple sound card for my music system, but from some days the sound is not so clear in the headphones. what i should have to do.?

---

### Post by osnaya on 2010-12-04
> **locksalordy said:**
> Hello Again,

Joy! After trying a full power down, the system came up with the sound card working as it ought.

Apologies for posting before doing this.

locksalordy

That worked for me too, thank you!

---


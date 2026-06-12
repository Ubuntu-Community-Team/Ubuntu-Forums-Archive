---
title: "How to control audio power save? Sound card keeps going off. Takes ages to wake."
date: 2011-12-18
forum: Multimedia Software
---

### Post by BFG on 2011-12-18
I'd much prefer that the sound card stays hot until I'm away from the computer, because the sleep/wake function of alsa seems flaky.

Sound works fine, but sometimes flash can't wake it - I have to run a media player.  Then after sound finishes playing after x seconds, the sound card goes to sleep again.

Can't find any settings - any tips on where to look?

11.04 64 bit

---

### Post by MoreOrLess on 2011-12-18
You put a line at the end of /etc/modprobe.d/alsa-base.conf like this (assuming you have a hda-intel compatible device):
```
options snd-hda-intel power_save=0
```

---

### Post by BFG on 2011-12-19
Hey thanks.  That started me on a solution.

I found this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201/comments/65](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201/comments/65)

> 
franco_bez (franco-bez) wrote on 2011-04-13:	 #65



I found that setting the Module-options

power_save=0
and
power_save_controller=N

in
/etc/modprobe.d/alsa-base.conf

get's overwritten in Natty in the file:

/usr/lib/pm-utils/power.d/intel-audio-powersave

I changed the line

INTEL_AUDIO_POWERSAVE=${INTEL_AUDIO_POWERSAVE:-true}
to
INTEL_AUDIO_POWERSAVE=false

Now Natty keeps the hda_intel adapter power_save settings as desired

---

### Post by MoreOrLess on 2011-12-19
You're welcome. Glad to see there's a workaround for shoddy BIOS work. Please mark thread solved.

---


---
title: "[SOLVED] sound possibly misconfigured...?"
date: 2008-11-06
forum: Multimedia Software
---

### Post by iPirates on 2008-11-06
Removed Vista on a new Asus m50 laptop, put on Ubuntu and I've got no sound.

Went through the comprehensive sound guide a few times, everything point towards the alsa mixer - which is what I think is misconfigured.

aplay -l brings up this:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
 Subdevices: 0/1
 Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
 Subdevices: 1/1
 Subdevice #0: subdevice #0

so the card is recognized from what I can see...

When trying to configure alsa, I can only fiddle with the master volume (which is not muted btw...).  There are no other controls.

Any thoughts?

---

### Post by iPirates on 2008-11-06
Found out the issue was alsa.  Drivers for my on board intel sound card weren't included in the release.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Followed the steps to recompile the newest alsa drivers (rc3 ones), sound works fine.

---

### Post by Yellow Pasque on 2008-11-06
The latest drivers are ALSA 1.0.18, not ALSA 1.0.18rc3 (i.e. the FTP site lists them alphabetically, not sequentially). I recommend using this script to install 1.0.18: [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)
It does a more thorough job of building the ALSA packages than the directions you followed and has an easy reinstall option (comes in handy after kernel updates).

I am contemplating changing the documentation to add the extra dependencies and to make sure ALSA lib gets compiled first.

---

### Post by iPirates on 2008-11-06
> **Temüjin said:**
> The latest drivers are ALSA 1.0.18, not ALSA 1.0.18rc3 (i.e. the FTP site lists them alphabetically, not sequentially). I recommend using this script to instal 1.0.18: [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)
It does a more thorough job of building the ALSA packages than the directions you followed and has an easy reinstall option (comes in handy after kernel updates).

Whops, hmm I'll have to fix that then.  Either way, I was happy about the sound being back :)

---


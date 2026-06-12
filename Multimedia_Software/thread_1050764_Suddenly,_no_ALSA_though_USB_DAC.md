---
title: "Suddenly, no ALSA though USB DAC"
date: 2009-01-26
forum: Multimedia Software
---

### Post by ilovesocks on 2009-01-26
Booted up Xubuntu 8.04 as usual a few days ago and could not get sound through my USB soundcard - it had worked just a few hours before! I neither made settings changes nor installed any updates. alsamixer shows normal volume levels on the device and asoundconf set-default-card PCM2702 (the device name, according to asoundconf list) has no effect. In fact, there seems to be no problem with communication between the OS and the hardware because the "Playback" light on the DAC lights up as it should whenever audio is playing (i.e. through MPlayer, VLC, gmusicbrowser, Firefox, etc.), but no sound comes out. So my audio device is the default - it's almost as if some hidden volume control is turned down, but it's not alsamixer and it's not the amp connected to the DAC.

ALSA through onboard works fine, though since testing it I have blacklisted snd-hda-intel in an effort to fix the problem. What's odd is that if I connect the device to my Windows XP guest through vmware, it works fine. Has anyone else had their USB sound device stop working lately, or perhaps can see what the problem is?

---

### Post by ilovesocks on 2009-02-06
bump

EDIT: In desperation, I tried adding the volume control to my Xubuntu panel. To my surprise, the volume slider for my DAC was all the way down, even though alsamixer claimed it was where it should be (~60%). I pulled up the slider and lo and behold, I had sound. So beware, if you think alsamixer is lying, check your DE's volume GUI!

**[SOLVED]**

---


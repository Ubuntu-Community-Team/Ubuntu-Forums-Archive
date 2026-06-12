---
title: "Very low sound - Xubuntu 11.04 &amp; RealTek ALC269."
date: 2011-08-30
forum: Multimedia Software
---

### Post by casbahdk on 2011-08-30
I am having problems getting the sound on an Xubuntu install to work properly. I added```
snd-hda-intel model=auto
```to /etc/modprobe.d/alsa-base.conf to get the sound to work at all, but even with all of the sound levels in alsamixer turned up to 100%, the sound is unreasonably low. I am using Xubuntu 11.04 and my netbook has a RealTek ALC269 sound card.

---

### Post by lidex on 2011-08-31
> **casbahdk said:**
> I am having problems getting the sound on an Xubuntu install to work properly. I added```
snd-hda-intel model=auto
```to /etc/modprobe.d/alsa-base.conf to get the sound to work at all, but even with all of the sound levels in alsamixer turned up to 100%, the sound is unreasonably low. I am using Xubuntu 11.04 and my netbook has a RealTek ALC269 sound card.

Change that line in alsa-base.conf to read:
```
options snd-hda-intel model=zepto
```
**Reboot**

---

### Post by casbahdk on 2011-09-04
That seem to have solved the issue, although I think the volume for some videos on YouTube is still way too low, even with the volume turned up to max both on the computer (master and speaker) and on the video itself.

---

### Post by .... on 2011-09-04
Make sure the application volume is maxed out in the volume control. I'm not sure what it looks like for Xubuntu, but you can always install pavolumecontrol and use that if Xubuntu doesn't show the per-application volumes associated with pulseaudio

---


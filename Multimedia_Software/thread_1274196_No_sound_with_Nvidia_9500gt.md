---
title: "No sound with Nvidia 9500gt"
date: 2009-09-24
forum: Multimedia Software
---

### Post by rickead2000 on 2009-09-24
Hi,

I have got an Nvidia 9500gt and cannot get any sound to come out of my mobo's onboard soundcard.

It's definately not a volume problem as if I remove the Nvidia card my sound works perfectly.  As soon as I plug it back in again, I lose sound.

I have this issue with and without any extra drivers installed.

Anybody know what could be causing the problem?  The applications appear to play, but nothing comes out.

# aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by rickead2000 on 2009-09-24
I've fixed it.

Looks like it might be a bug in Ubuntu 

I needed to add "options snd-hda-intel probe_mask=1" to the bottom of /etc/modprobe.d/alsa-base.conf in order for it to work in the presence of an NVidia card.

I then needed to reboot, unmute the sound (which it seemed to have muted) and turn up the "Front" channel which had appeared

---


---
title: "Weird Sound Issue"
date: 2009-09-07
forum: Multimedia Software
---

### Post by gamechampionx on 2009-09-07
I'm currently running Kubuntu 9.04.  The sound doesn't seem to be working correctly.

When I log in or out, I get the standard noises but everywhere else, my sound does not work.  I've tested in VLC (DVDs and CDs), and on the web (Youtube) and get absolutely no sound.

I've made sure my Alsamixer had its volume pumped in every which way.

aplay -l gives:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I'm wondering if this issue is indicative of a specific type of problem.  Help is appreciated.

---

### Post by gamechampionx on 2009-09-07
Some additional info:

This problem happened after I installed libdvdcss2 (which is legal in my country) to get DVD codecs to work.  I installed it using: "sudo /usr/share/doc/libdvdread4/install-css.sh".  DVD playback and sound was working until I restarted - then all sound except for the default Ubuntu noises had died.

I'm thinking this could just be a matter of using the wrong sound device but I'm not sure where I can find that info in Kubuntu.

---


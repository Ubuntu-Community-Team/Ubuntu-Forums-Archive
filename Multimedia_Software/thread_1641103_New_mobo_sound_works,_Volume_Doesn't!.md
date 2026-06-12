---
title: "New mobo: sound works, Volume Doesn't!"
date: 2010-12-08
forum: Multimedia Software
---

### Post by Ken_g6 on 2010-12-08
So I've been running Ubuntu 9.04 on a Gigabyte G32M-ES2L for over a year.  It was working fine.  Then I accidentally scratched the board and had to replace it with another one.  It's the same brand and model; though it looks just slightly different.  I also pulled out an extra modem I wasn't using; I saw mention of modems somewhere around here.

Anyway, now when I try to change the volume globally, it doesn't work very well.  Of my two device options listed by aplay -l:
```
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Only changing the single volume slider available on the first seems to have any effect.  And often that seems to get overridden or reset or something.

Now when I start alsa-utils, this is what I get:
```

 * Setting up ALSA...                                                            * warning: 'alsactl restore' failed with error message 'Unknown hardware: "HDA-Intel" "Realtek ALC887" "HDA:10ec0887,1458a002,00100302" "" ""
Hardware is initialized using a guess method
/usr/share/alsa/init/default:23: control element not found
/usr/share/alsa/init/default:35: control element not found
alsactl: set_control:1266: failed to obtain info for control #1 (Invalid argument)
alsactl: set_control:1266: failed to obtain info for control #3 (Invalid argument)
alsactl: set_control:1266: failed to obtain info for control #5 (Invalid argument)
alsactl: set_control:1266: failed to obtain info for control #6 (Invalid argument)
alsactl: set_control:1266: failed to obtain info for control #9 (Invalid argument)
alsactl: set_control:1266: failed to obtain info for control #38 (Invalid argument)'...                                                                         amixer: Mixer hw:0 load error: Invalid argument

```
Followed by more of that last line, followed by a bunch of lines with "Invalid card number.", each of which is followed by the usage for amixer.

I tried a few things from the Comprehensive Sound Problem Solutions Guide that seemed logical, but haven't helped:

- I added "options snd_hda_intel index=0" to an empty (or was it nonexistant) /etc/modprobe.d/alsa-base.
- I added myself to the audio group.

One more thing: I've seen directions to remove and reinstall ALSA; but it looks like that might involve removing gdm as well.  I *just* got gdm configured the way I want it in another thread; I'd rather stick with what I've got than risk losing that. :o

---


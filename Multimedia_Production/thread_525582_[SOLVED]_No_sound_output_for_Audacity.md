---
title: "[SOLVED] No sound output for Audacity"
date: 2007-08-14
forum: Multimedia Production
---

### Post by leo_rockway on 2007-08-14
Hello everyone, I have this pretty interesting issue with Audacity.

When I try to play a file with Audacity no sound comes out. I get no errors at all and I can see the green bars moving as if Audacity were playing something.

* My sound works perfectly in every other application.

* I'm on KDE.

* I tried aoss audacity too, and that didn't work either.



My Audacity settings:
Audio I/O
Playback device: ALSA: HDA Intel: STAC92xx Digital (hw:0,1)
Recording device: ALSA: HDA Intel: STAC92xx Analog (hw:0,0)


> aplay -l
**** PLAYBACK list of Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


> cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).

> lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)


Recording doesn't work either, but I think working on one problem at a time would be the best.

Thanks in advance!

---

### Post by dabl on 2007-08-14
Yep, I've got that Intel HDA system too.  Audacity is "touchy".

First shut down anything else that might want to use the sound system, like Firefox or Amarok.  Give it 30 seconds, then open Audacity.  Check "Edit>Preferences" and click the I/O tab.  On "Output" it should say "ALSA" when it's ready to go.

You also might need to twiddle your ALSA Mixer. "Edit>Preferences" and check every box on the list.  :)

---

### Post by leo_rockway on 2007-08-16
thanks for your help dabl...

i decided to update to gutsy and now audacity plays sounds without any problem!

i still have to make it record, but that's not an audacity problem. i still have to make kubuntu recognize my mic.

---

### Post by dabl on 2007-08-16
Hmmmm ... sounds good -- maybe I should be installing Gutsy!

:lolflag:

---


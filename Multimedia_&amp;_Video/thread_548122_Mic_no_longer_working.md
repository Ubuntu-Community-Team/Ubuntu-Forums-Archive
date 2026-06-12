---
title: "Mic no longer working"
date: 2007-09-10
forum: Multimedia &amp; Video
---

### Post by dcroxton on 2007-09-10
My microphone stopped working sometime; I'm not sure exactly when, because I don't use it that often, but I first noticed it yesterday.  Sound plays fine.  The mic is hard to test because gnome-sound-recorder crashes (segmentation fault) when I try to record, and Audacity gives me the "can't open input device" error.  (I noticed the problem when I tried to use Gizmo.)

In accordance with the "Comprehensive Sound Problem Solution Guide," I have done the following:
[LIST]
[*]Checked that the microphone is not muted and has volume up
[*]Re-installed linux-sound-base, alsa-base, and alsa-utils
[*]Tried to recompile the drivers from the ALSA project, but got errors
[/LIST]

I've also tried with and without esd and jack running.  I have an intel8x0 chipset soundcard, with an mpu401 chipset also on a Hauppauge tv capture card.  (I've never had a problem with the sound getting mixed up between the cards before.)  Here is what I get from arecord -l:
```
**** List of CAPTURE Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 1: Intel ICH - MIC ADC [Intel 82801DB-ICH4 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 2: Intel ICH - MIC2 ADC [Intel 82801DB-ICH4 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 3: Intel ICH - ADC2 [Intel 82801DB-ICH4 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I'm a bit puzzled by the presence of two entries for microphones.  It doesn't make any sense to me, but maybe it is some technical thing that I don't understand.  When I run alsamixer (but not alsamixergui or the gnome alsa mixer), there is a column labelled "Mic Sele" that shows "Mic2" above it; I haven't figured out how to change it.

I tried to test recording using arecord, but nothing happened (the file was not even created).  I figured this might be because I didn't specify a device, but I couldn't figure out the name of the microphone devices revealed in arecord -L.

As always, any help is appreciated.  It's almost more frustrating that it used to work fine, since I know there is some configuration thing I can change to make it work, I just don't have any idea what it is.

Sincerely,
Derek

---


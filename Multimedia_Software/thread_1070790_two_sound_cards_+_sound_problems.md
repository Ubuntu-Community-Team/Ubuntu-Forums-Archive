---
title: "two sound cards + sound problems"
date: 2009-02-15
forum: Multimedia Software
---

### Post by Durrock on 2009-02-15
Hi all -

I've been having a hard time getting sound under Ubuntu.  Following some of the guides here, I think I've got it working using PulseAudio, but now, its only working on the onboard sound from the motherboard. I really want to use my PCI soundcard.  How do I get pulseaudio to use my other sound card rather than the built in one?
Heres' the details from aplay -l:
```

card 0: CS46xx [Sound Fusion CS46xx], device 2: CS46xx - IEC958 [CS46xx - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CS46xx [Sound Fusion CS46xx], device 3: CS46xx - Center LFE [CS46xx - Center LFE]

card 1: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I want sound from the CS46xx card.  It's the PCI based card. The IntelICH5 one is the builtin.
If I go into sound preferences, and select, Pulseaudio server for sound playback device, I *only* get sound when my speakers are plugged into my onboard soundcard.  If I change it to soundfusion cs46xx (alsa) I get an error message "could not open audio device for playback".

Any ideas? This is very confusing.

---

### Post by markbuntu on 2009-02-15
Go here first

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If that does not help you figure out your problem you need to go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---


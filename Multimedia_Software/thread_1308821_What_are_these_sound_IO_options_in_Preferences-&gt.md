---
title: "What are these sound IO options in Preferences-&gt;Sounds?"
date: 2009-10-31
forum: Multimedia Software
---

### Post by OrangeVixen on 2009-10-31
I'm not an expert on sounds, and I know that these work, but I was wondering if anyone can explain what they are?

In Preferences->Sounds, I have Autodetect as an option, that works for most cases, but I want to know what are the other things I can select and what do they do:

Autodetect
HDA Intel ALC889 Digital (ALSA)
HDA Intel ALC889 Analog (ALSA)
HDA Intel ALC889 Analog (OSS)
HDA Intel ALC889 Analog (OSS)
HDA Intel ALC889 Analog (OSS)
ALSA
OSS
PulseAudio Sound Server


More info:

user@zareason-limbo:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by OrangeVixen on 2009-11-01
Bump, anyone know why the OSS one is listed 3 times?

---

### Post by Yellow Pasque on 2009-11-01
> **OrangeVixen said:**
> Bump, anyone know why the OSS one is listed 3 times?

Do you have surround sound? I'm using OSS4 with a 5.1 card and it lists the front, center/lfe, and surround outputs separately. Anyway, you'll generally want to use PulseAudio (or autodetect, which should output to pulse).

---

### Post by OrangeVixen on 2009-11-01
Yes, I have a 5.1 sound card and 5.1 speakers, it's hard for me to tell the difference just by clicking on Test. I hear the test sound on all the speakers for first two OSS settings but no sound at all on the 3rd OSS setting.

I'll set them all to PulseAudio Sound Server then I guess until I find an error or a problem, thanks.

---


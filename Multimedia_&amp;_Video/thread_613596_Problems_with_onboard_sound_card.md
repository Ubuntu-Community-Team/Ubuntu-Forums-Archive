---
title: "Problems with onboard sound card"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by pr0b on 2007-11-15
Hi!
I have the following problem. I have 2 sound cards: PCI and onboard. I am using PCI to play all sounds and onboard with headset to work with skype. The problem is that onboard sound card doesn't work.
Here is the output of the cat /proc/asound/modules:
 0 snd_ca0106
 1 snd_hda_intel
 2 saa7134_alsa

(the last one is tv tuner)

the output of the aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I made changes in the /etc/init.d/alsabase to load first PCI sound card, then onboard and tv tuner
Skype works great with PCI card but when i choose onboard card, there is no sound.
Also i've tried to make onboard card to be the default one and there were no sounds at all.
I would appriciate any help
Thank you

---

### Post by pr0b on 2007-11-16
In case if someone who knows the solution missed my message. Maybe someone could provide me some tips, it would be enough for me. Thanks

---


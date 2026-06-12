---
title: "Live CD, mulitple sound card problems!!"
date: 2008-07-24
forum: Multimedia Software
---

### Post by Tibco on 2008-07-24
Hi, i think i have a big problem on my hands here. When i ran Gutsy Live CD, i could hear the start up drums and the sound seemed to work fine, i checked under the sound tab and the "autodetect" setting worked fine. However, when i installed it, i could not hear any system sounds at all and .wav files only played when i changed the driver and even then, it only worked under totem, not mplayer or VLC. Help! I upgraded to hardy and i still have the same problem. Is it possible to load the exact same drivers as the Live CD on a hard drive install?

Here is a list of my sound cards.
```
 cat /proc/asound/modules
 0 snd_cmipci
 1 saa7134_alsa
 2 snd_via82xx

```

Help!

---

### Post by Tibco on 2008-07-25
fixed it by diableing the integrated sound card through bios, manually taking out the tv tuner and doing a clean install of ubuntu.

---

### Post by cariboo on 2008-07-25
The saa7134-alsa is for you TV tuner card. The snd_via82xx looks like your builtin sound card. Double click the speaker icon in the top right panel, this will bring up the volume control panel make sure via82xx is selected, and you should be OK.

Jim

---


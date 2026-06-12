---
title: "Unable to control OSS Volume Level"
date: 2006-01-24
forum: Multimedia &amp; Video
---

### Post by SirNuke on 2006-01-24
Even as an experienced Linux user, this issue has been driving me insane over the past couple of days.  When ever a program uses ALSA or esd to output sound it correctly observes the volume levels.  However, when a program outputs using OSS it plays the sound at the max volume level.  Inside the gnome volume control panel, there is an option to change device, between an alsa mixer and oss mixer.  Under the OSS Mixer, the only output volume bar is PCM.  The slider, however, only moves between mute (or no volume) and full volume.

The two devices are
NVidia CK8S (Alsa)
C-media electronics cmi9761 (OSS)

It is an integrated sound card of the Chaintech motherboard VNF3-350

Any ideas?  I thought alsa emulated OSS, so this wouldn't be an issue...

---


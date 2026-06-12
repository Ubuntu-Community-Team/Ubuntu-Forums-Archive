---
title: "MAUDIO 2496 audiophile not working in 12.04 64bit"
date: 2012-06-07
forum: Multimedia Software
---

### Post by meatychunks on 2012-06-07
Hi,

I had the above soundcard working without any problem in 10.04. However, after a recent upgrade to 64 bit mythbuntu 12.04, I cannot get a squeak out of it.

There's no pulseaudio installed, alsa mixer has volume levels up - I simply cannot get it to work.

aplay -l gives me this:
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
The on-board sound is disabled in the BIOS.

Don't know if this is a generic ubuntu 12.04 thing, or whether it's specific to mythbuntu.

Any help appreciated.

---

### Post by Ruhani04 on 2012-10-06
Just install envy24 control via software center.
Open after installation and go to "analog volume" tab. Move the two volume sliders to your liking and sound should work fine.
I have been doing this several times in different Ubuntu/Lubuntu/Xubuntu installs.

---


---
title: "Sound problem after install Catalyst with VA-API"
date: 2011-05-02
forum: Multimedia Software
---

### Post by smkdesign on 2011-05-02
Hi

After installing Catalyst with VA-API began a strange problem with the sound via HDMI.

Prior to installing the sound worked fine.

Platform: MSI E350IA-E45 with Radeon HD 6310 and AMD Zacate E350
Version of Catalyst 11.4

After installing the sound is playing with a terrible noise

Sample: [https://rapidshare.com/files/460283529/sound.wav](https://rapidshare.com/files/460283529/sound.wav)

I already tried all the audio outputs, but this does not solve the problem. The problem occurs only when the transmission of sound through HDMI

Thanks

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0

---

### Post by Ellimist on 2011-07-07
I use the same motherboard on Xubuntu 11.04, with sound via HDMI (card 0, device 3), and I get no noise. VA-API has nothing to do with this, though.

PS: I'm using Catalyst 11.6, not 11.4, if that helps.

---


---
title: "SPDIF stopped working - device no longer available?"
date: 2009-11-13
forum: Mythbuntu
---

### Post by stdPikachu on 2009-11-13
Been running an SPDIF device successfully since a fresh install of the RC... but for some reason ALSA is now defaulting to the HDMI device instead of the digital out and I can't seem to get it back. Hardware is a P5N7A-VM using the onboard Intel HDA which has an integrated SPDIF output.
```
banquo@banquo:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
Hence /etc/asound.conf is configured as follows to default to card0 device1:
```
pcm.!default {
        type hw
        card 0
        device 1
}
```
Yet alsamixer will only display the HDMI device; as such I've got no sound over either my digital or analogue outputs. I'vre tried editing the device number to try and get analogue working, but setting device 0 also shows only the HDMI output.

Does anyone know why this has happened or what I can do to get my SPDIF output back?

---

### Post by stdPikachu on 2009-11-14
Hmm. After a) copying the /etc/asound.conf to ~/.asoundrc b) rebooting and c) leaving the computer in the presence of some drunken partygoers for a couple of hours, the music pumping out of it is managing to keep me awake... so I'm going to temporarily mark this as solved pending further investigation tomorrow.

Nowt else has changed - alsamixer still seems to be telling me I'm using the HDMI device - so a bit of an odd one.

---


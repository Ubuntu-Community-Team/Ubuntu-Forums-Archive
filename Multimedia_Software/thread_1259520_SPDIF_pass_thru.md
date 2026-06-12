---
title: "SPDIF pass thru"
date: 2009-09-06
forum: Multimedia Software
---

### Post by ben83 on 2009-09-06
Hi all, 

I am using an ASUS P5E-VM HDMI board and I am really quite happy with my ubuntu setup. Recently I got hold of an nvidia 9500GT card which has an HDMI output. There is a cable that came with the card to plug into the mother for sound.

Whilst my graphics are working fine I cannot seem to get audio over HDMI. I have plugged the cable into my mainboard spdif connectors and when I do aplay -D hw:0,1 I don't get any sound. 

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I checked alsamixer and all devices are unmuted and turned up to max.

Anyone got any pointers as to what I could try next?

Thanks in advance, 
Ben

---


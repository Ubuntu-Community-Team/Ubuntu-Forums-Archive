---
title: "Audio over HDMI with 8400GS"
date: 2010-09-04
forum: Multimedia Software
---

### Post by Matters1 on 2010-09-04
Hi,

I am having some trouble getting Ubuntu (Lucid) to recognise that my NVidia 8400GS (one of the newer ones with and HDMI plug integrated into the card) is an option for sound output, not the one that needs a cable form the motherboard spdif out.

I have read heaps of info about getting various NVidia cards to output sound over HDMI and have managed to upgrade to the latest Alsa (1.0.23), tried different NVidia drivers (currently using 195 I think) and still nothing.

aplay -l only shows my onboard sound card and I can't seem to locate things like sound.conf in etc/modprobe.d 

aplay -l output:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Has anyone else managed to overcome this problem?

This is for a HTPC running XBMC so having audio and video over the one cable would be the aim and since the motherboard doesn't have optical audio out this appears the only way to get surround sound.

Does anyone know how I can get the video card to be recognised as an audio output?

Any help would be much appreciated.

---

### Post by Matters1 on 2010-09-05
UPDATE:

I am a tard, this card still needs a cable from motherboard SPDIF out, it is just that the hide it better and there wasn't a cable included with my card.

Hopefully I will get this working after a trip to get some parts.

---

### Post by modafokaxx on 2010-09-20
Uhh the 8400 is far from being a recent card, I have it in my 2008 laptop.
In computer hardware time, that's generations...

Anyway, there *is* a bug, [#389494]("http://[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/389494"), relating to the no sound over HDMI issue some are experiencing with a 8400 GS card. So you were right to complain! ;)

Looks like it's fixed in Maverick, so that's nice.

Using IEC958 digital output is a nice option too, but doesn't exactly solve the sound over HDMI issue. Still, good to see you found a workaround. :)

---

### Post by Matters1 on 2010-09-20
Good to know, thanks.

I meant a newer revision of the GS card that has HDMI not s-video, I know it is old tech. In fact that was the point, where else can I get a card that supports VDPAU for $32?

As it turns out the motherboard I have doesn't have any S/PDIF headers to connect the cable to anyway!

---


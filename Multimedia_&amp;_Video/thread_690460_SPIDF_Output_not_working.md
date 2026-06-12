---
title: "SPIDF Output not working"
date: 2008-02-07
forum: Multimedia &amp; Video
---

### Post by Potted Plant on 2008-02-07
Hello,

I am having some trouble getting the SPIDF optical audio out working on my system. I am having no trouble with the analog audio, but there is no digital. There is no audio anywhere- no system notification sounds, no audio in VLC, Amarok, etc..There is no signal getting to the receiver (it reports "unlocked"). The red laser diode isn't even on behind the dust flap.

Motherboard: ASUS M2N32-SLI Deluxe, AMD X2 6400+, 4GB RAM, Ubuntu 7.10 x86-64 edition.

Anybody have any ideas?

-Steve

---

### Post by tgalati4 on 2008-02-07
What is the sound chip on your board?

>aplay -l

For example:

>aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


You may need to use a switch such as: (in /etc/modprobe.d/alsa-base)

options snd-hda-intel model=6stack-digout

*digout* activates the digital port capability and you need to go into volume-mixer and activate the appropriate digital switch.

---


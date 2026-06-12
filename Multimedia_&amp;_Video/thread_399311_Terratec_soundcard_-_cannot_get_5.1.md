---
title: "Terratec soundcard - cannot get 5.1"
date: 2007-04-02
forum: Multimedia &amp; Video
---

### Post by haku.spejsr on 2007-04-02
Hi every1! I have a soundcard problem. my soundcard is terratec aureon space, supporting 7.1 sound. I don't need that, I need only the 5.1 sound and I'll be satisfied. 

I have already installed alsa driver and oss manually.

Alsa mixer shows all channels needed for 7.1 and they seem ok, I muted ones that I don't need (6th and 7th) but this is irrelevant (I guess).

This is the aplay -l output:

**** List of PLAYBACK Hardware Devices ****
card 0: T71Space [Terratec Aureon 7.1-Space], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: T71Space [Terratec Aureon 7.1-Space], device 1: IEC1724 IEC958 [IEC1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: T71Space [Terratec Aureon 7.1-Space], device 2: ICE1724 Surrounds [ICE1724 Surround PCM]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2

On the sound preferences menu, apart from alsa, oss, esd I can chose between ICE1724, that brings out stereo output, and is the one that works at this point, and two more: ICE1724 IEC958 (don't know what this is) and ICE1724 surround. if I try to test pipes for on the later, which I suspect could be the 5.1, the whole sound dialogue crashes. So, I am testing this with a 5.1 dvd from vlc and xine from amarok and they both give only 2 channels even when selected 5.1 surround.

at this point I would also like to know if there is a speaker testing utility available.

I tried reinstalling drivers but to no avail. help needed! 

ty very much in advance

---


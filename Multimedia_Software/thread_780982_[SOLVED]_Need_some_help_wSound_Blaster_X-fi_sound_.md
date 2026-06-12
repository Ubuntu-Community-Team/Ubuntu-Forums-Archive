---
title: "[SOLVED] Need some help w/Sound Blaster X-fi sound card"
date: 2008-05-03
forum: Multimedia Software
---

### Post by tad1073 on 2008-05-03
I just bought a sound card and it is not bein detected. Can someone give me a hand?

```
00:03.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs X-Fi Platinum
	Flags: bus master, medium devsel, latency 64, IRQ 28
	I/O ports at 2000 [size=32]
	Memory at b1600000 (64-bit, non-prefetchable) [size=2M]
	Memory at b4000000 (64-bit, non-prefetchable) [size=64M]

```

---

### Post by Yellow Pasque on 2008-05-03
I recommend you return the card and get one that's more compliant with Linux and made by a company less evil than Creative.

---

### Post by phyrre on 2008-05-04
X-FI cards don't work on 8.04 with alsa yet. You'll have to set up oss instead:

[http://ubuntuforums.org/showthread.php?t=780961&highlight=oss](http://ubuntuforums.org/showthread.php?t=780961&highlight=oss)

---

### Post by tad1073 on 2008-05-04
I can't get my sound to work after the install.
BTW, I am connecting the audio to a Yamaha RX V-361 receiver
```
:~$ aplay -l


********************   WARNING   *******************************
Warning! aplay uses ALSA emulation instead of the native OSS API
****************************************************************

**** List of PLAYBACK Hardware Devices ****
card 1: snd_ctl_card_info_get_id [Sound Blaster X-Fi (SB046x/067x/076x)], device 0: OSS ID [Sound Blaster X-Fi (SB046x/067x/076x) output]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Sound Blaster X-Fi (SB046x/067x/076x)], device 1: OSS ID [Sound Blaster X-Fi (SB046x/067x/076x) input]
  Subdevices: 1/1
  Subdevice #0: OSS subname

```

---

### Post by pickboy87 on 2008-05-04
I had the X-Fi card for a while and I never got it to work in Ubuntu...as far as I know, it was never supported and the only driver they ever released for it was a 64 bit driver thats in it's alpha stage. My suggestion would be to return that card ASAP if you can and get something linux friendly (I have the M-Audio Revolution 5.1, it works in Linux, but I'm having some minor difficulties with it).

---

### Post by tad1073 on 2008-05-04
I returned it. I think I am going to wait and save some money so I can buy a new computer.

---


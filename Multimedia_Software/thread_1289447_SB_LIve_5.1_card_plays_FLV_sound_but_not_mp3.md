---
title: "SB LIve 5.1 card plays FLV sound but not mp3"
date: 2009-10-12
forum: Multimedia Software
---

### Post by somitras on 2009-10-12
I have installed Ubuntu 9.04 recently. I am able to play sound from FLV files, but wav, mp3, mpeg files do not produce any sound. Only video plays in gmplayer or Totem. In "Volume Control->Switches->SB Live Analog/Digital Output Jack", if I toggle the tick (select it) then very weak sound (with a lot of noise) can be heard from the mp4 files. But there is no sound from mp3 (or at least I can't understand it in the noise) at all. 

Output from "aplay -l"
-----------------------
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [SB Live 5.1], device 0: emu10k1 [ADC Capture/Standard PCM Playback]

..... many more lines like this


(2) Output from "lspci -v"
-------------------------
.....
.....
06:01.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
	Subsystem: Creative Labs Device 8064
	Flags: bus master, medium devsel, latency 32, IRQ 22
	I/O ports at 1080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1
......
......

Any help is greatly appreciated.

---

### Post by salar on 2009-11-03
I have the same problem. I'm new to Ubuntu and have leapt in at 9.10 and have been having trouble getting my SB Live! soundcard to work. At the moment, all I have access to is the PC soundcard. When I also do the aplay-i command I get...

card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [SB Live! 5.1 [SB0220]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Live [SB Live! 5.1 [SB0220]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Live [SB Live! 5.1 [SB0220]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So, as far as I can gather the SB card is recognised but I can't activate it. Any ideas?
John

---

### Post by somitras on 2009-11-04
What happened to the forum ? No one seems to be helping the two of us. Both of us having sound problem with a standard SB Live 5.1 sound card from Creative. 

Any help to resolve this is greatly appreciated. Thanks.

---


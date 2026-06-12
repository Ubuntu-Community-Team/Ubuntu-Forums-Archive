---
title: "Poor sound quality and no stereo with intel HDA"
date: 2014-07-11
forum: Multimedia Software
---

### Post by jimmeu on 2014-07-11
Hi,

I just installed 14.04 on a computer. 
With headphones plugged (front or back plug, same result), I don't have any stereo : in sound parameters / test sound, left test and right test produce sounds in both ears.
Moreover, when I listen to music the sound quality is very poor and it seems the bass is almost non existant.

My card is an integrated Intel HDA with ALC269VB chipset :

aplay -l
**** Liste des Périphériques Matériels PLAYBACK ****
carte 0: PCH [HDA Intel PCH], périphérique 0: ALC269VB Analog [ALC269VB Analog]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: NVidia [HDA NVidia], périphérique 3: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: NVidia [HDA NVidia], périphérique 7: HDMI 1 [HDMI 1]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0

Any help would be much appreciated.

---

### Post by tgalati4 on 2014-07-11
Did you try multiple headphones?  If you have a damaged cord on your headphones, you can get a mono sound on any source.  Try with a phone or iPod and see if the headphones are working correctly.

---

### Post by jimmeu on 2014-07-15
The headphones work perfectly with another source, the problem is not there.

---

### Post by dfouch on 2014-11-30
i'm having this same issue with an integrated Intel sound board. I'm curious if you ever resolved your issue. I'm not having much luck finding a solution. It also seemed to work in the past. I believe this may be a 14.04.01 issue.

Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
	Subsystem: Dell Device 04ed
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at fe700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel


00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
--
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6400 Series]
	Subsystem: Pegatron Device aa98
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at fe640000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel

---


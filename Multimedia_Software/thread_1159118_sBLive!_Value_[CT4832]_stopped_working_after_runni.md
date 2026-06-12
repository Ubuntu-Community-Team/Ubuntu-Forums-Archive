---
title: "sBLive! Value [CT4832] stopped working after running asoundconf set-default-card"
date: 2009-05-14
forum: Multimedia Software
---

### Post by 0graham0 on 2009-05-14
Hi,

I just installed Ubuntu 9.04 x64 and everything was working perfectly except for an external USB headset. I followed instructions to use the following command to get the head set working. ```
asoundconf list
Live
Headset
asoundconf set-default-card Headset
```After running this command all sound stopped working through my sound card, even after running: ```
asoundconf set-default-card Live
```

Any help getting sound working again would be greatly appreciated.

Here is the info on my sound card:

```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SBLive! Value [CT4832]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Live [SBLive! Value [CT4832]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SBLive! Value [CT4832]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
```
lspci -v
...
02:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
	Subsystem: Creative Labs Device 8027
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at 8400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1
...
```

---

### Post by 0graham0 on 2009-05-14
So, rather embarrassingly, it turns out my sound was just muted.

I went to Volume Control -> and unmuted PCM sound.

---


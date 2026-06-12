---
title: "[SOLVED] Losing Sound"
date: 2007-08-17
forum: Multimedia &amp; Video
---

### Post by jusmurph on 2007-08-17
When i launch alsamixer, it goes straight to the NVidia CK804  Device. This has only happened since the sound has stopped working in some programs.

I have tried setting the Audigy2 as default via:

```
sudo asoundconf set-default-card Audigy2
```

Which as far as i can tell does nothing?


```
**anth@smurph:~$ aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

[B]
anth@smurph:~$ sudo cat /proc/asound/modules[/B]
Password:
 0 snd_intel8x0
 1 snd_emu10k1


[B]
anth@smurph:~$ sudo cat /proc/asound/pcm[/B]
00-02: Intel ICH - IEC958 : NVidia CK804 - IEC958 : playback 1
00-01: Intel ICH - MIC ADC : NVidia CK804 - MIC ADC : capture 1
00-00: Intel ICH : NVidia CK804 : playback 1 : capture 1
01-04: p16v : p16v : playback 1 : capture 1
01-03: emu10k1 : Multichannel Playback : playback 1
01-02: emu10k1 efx : Multichannel Capture/PT Playback : playback 8 : capture 1
01-01: emu10k1 mic : Mic Capture : capture 1
01-00: emu10k1 : ADC Capture/Standard PCM Playback : playback 32 : capture 1
anth@smurph:~$ 
```

---

### Post by jusmurph on 2007-08-18
It worked after i disabled my onboard soundcard in the bios!

---


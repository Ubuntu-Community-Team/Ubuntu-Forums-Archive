---
title: "iec958 digital outputs to analog speakers"
date: 2010-10-23
forum: Multimedia Software
---

### Post by dread22 on 2010-10-23
I'm trying to get my Audigy 2 Value to output digital but when I try to use the iec958 interface it outputs to the front speakers analog outputs, ie not the digital io socket.

I can get 5.1 surround by using the plug:surround51 device.

Have gone though other guides trying to fix the problem but no luck. Help would be appreciated to get the digital stuff working. I have included some outputs.

```
$aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [SB Audigy 2 Value [SB0400]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Audigy2 [SB Audigy 2 Value [SB0400]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [SB Audigy 2 Value [SB0400]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
$aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Audigy2
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    Default Audio Device
front:CARD=Audigy2,DEV=0
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=Audigy2,DEV=0
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=Audigy2,DEV=0
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
side:CARD=Audigy2,DEV=0
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    Side speakers
surround40:CARD=Audigy2,DEV=0
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Audigy2,DEV=0
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Audigy2,DEV=0
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Audigy2,DEV=0
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Audigy2,DEV=0
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Audigy2,DEV=0
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    IEC958 (S/PDIF) Digital Audio Output
```

---

### Post by dread22 on 2010-10-25
Bump?

---

### Post by lidex on 2010-10-25
> **dread22 said:**
> Bump?

Have you checked the digital/analog switch in alsamixer/gnome-alsamixer?

---

### Post by dread22 on 2010-11-05
> **lidex said:**
> Have you checked the digital/analog switch in alsamixer/gnome-alsamixer?

Yes tried changing the d/a switch via alsamixer, no change besides disabling my front analogue output (while the channels still worked). Gave up on digital and ended up using the 3 analogue outputs.

thx for the reply.

---


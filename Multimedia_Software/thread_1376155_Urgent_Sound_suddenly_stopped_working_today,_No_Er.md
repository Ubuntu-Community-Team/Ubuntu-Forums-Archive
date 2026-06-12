---
title: "Urgent: Sound suddenly stopped working today, No Error Messages"
date: 2010-01-08
forum: Multimedia Software
---

### Post by Amurko on 2010-01-08
OK, sound has been working fine on this machine for 3+ years and it stopped working right now.  I've not installed anything new today and I suspect a hardware problem.

- Tried rebooting: No Go
- Tried killing pulseaudio and restarting it: No Go
- Tried going into alsamixer and unmuting everything: No Go
- Tried reinstalling Alsa: No Go
- Tried plugging into every port on my sound card: No Go
- Tried plugging a working headphone (verified on another equipment) into every port on my sound card: No Go

I even tried going into my BIOS, enabling the 2nd on-board sound card, plugging the speakers in, and that too refuses to emit any sound!

Get this: I go into Applications -> PulseAudio Volume Control -> Output Devices

and then play a Youtube video, the sound "indicator" pulses along as if a sound is playing but no sound comes out of my speakers.  Apparently, my system thinks there's nothing wrong with the sound but no sound plays!


Here are some of my outputs:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [Unknown]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Audigy [Audigy 1 [Unknown]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [Unknown]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

aplay -l

```
speaker-test

speaker-test 1.0.20

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 192 to 2097152
Period size range from 64 to 699051
Using max buffer size 2097152
Periods = 4
was set period_size = 524288
was set buffer_size = 2097152
 0 - Front Left
Time per period = 11.350416
 0 - Front Left
Time per period = 11.332000
 0 - Front Left

```

---


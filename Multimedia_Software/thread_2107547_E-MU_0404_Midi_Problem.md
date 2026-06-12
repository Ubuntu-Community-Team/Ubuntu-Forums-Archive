---
title: "E-MU 0404 Midi Problem"
date: 2013-01-22
forum: Multimedia Software
---

### Post by Clockmender on 2013-01-22
Hello

I have tried again with Ubuntu to get my E-MU 0404 working but success is limited.

aplay -l gives me this:

**** List of PLAYBACK Hardware Devices ****
card 0: EMU0404 [E-mu 0404b PCI [MAEM8852]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: EMU0404 [E-mu 0404b PCI [MAEM8852]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: EMU0404 [E-mu 0404b PCI [MAEM8852]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

aplaymidi -l gives me this:

 Port    Client name                      Port name
 17:0    Emu10k1 WaveTable                Emu10k1 Port 0
 17:1    Emu10k1 WaveTable                Emu10k1 Port 1
 17:2    Emu10k1 WaveTable                Emu10k1 Port 2
 17:3    Emu10k1 WaveTable                Emu10k1 Port 3

You will notice there is no 

 Port    Client name                      Port name
         EMU10K1 MPU-401 (UART)           EMU10K1 MPU-401 (UART)

entry or midi though either!

Doing this, which apparently is required,:

modprobe snd-seq-midi

Gets me this:
[COLOR="Red"]
FATAL: Module snd_sq_midi not found.[/COLOR]

and I cannot see from the net where this comes from....

Doing this:

cat /proc/asound/oss/sndstat

Gets me this:

Sound Driver:3.8.1a-980706 (ALSA v1.0.25 emulation code)
Kernel: Linux Beastie 3.5.0-22-generic #34-Ubuntu SMP Tue Jan 8 21:41:11 UTC 2013 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
E-mu 0404b PCI [MAEM8852] (rev.0, serial:0x40021102) at 0xdc00, irq 21

Audio devices:
0: ADC Capture/Standard PCM Playback (DUPLEX)

Synth devices:
0: Emu10k1

Midi devices:
0: Audigy MPU-401 (UART)

Timers:
7: system timer

Mixers:
0: SB Audigy

Can someone tell me what I did wrong or haven't done please?

I have sound out but no Readable Clients/Output ports on Jack Connection Kit.

So near yet so far..........

---


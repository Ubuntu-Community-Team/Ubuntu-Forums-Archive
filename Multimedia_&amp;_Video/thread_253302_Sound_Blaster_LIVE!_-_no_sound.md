---
title: "Sound Blaster LIVE! - no sound"
date: 2006-09-08
forum: Multimedia &amp; Video
---

### Post by radone on 2006-09-08
I have sundcard SBLive! Value [CT4832] that gives sound with some noise in 1/2 sec intervals (sampling problem??).

If I install package ld10k1 - ALSA emu10k1/2 patch loader 
I got even no sound :-/

And even better - if I uninstall ld10k1 package in lsmod it is also included ?!?!?!

According to ALSA Matrix:
```
Sound Blaster Live emu10k1 	[ANio] [MIDIio] (1) (3)
(1) Output always resampled to 48khz.
(3) Hardware mixing supported
**Date Wednesday 02 March 2005 11:10**

```

So I guess it should be supported. ](*,) 


Please - if anyone could help, it would be really, really appreciated.

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: Live [SBLive! Value [CT4832]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32
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

```
lspci -v
```
0000:05:04.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
        Subsystem: Creative Labs CT4832 SBLive! Value
        Flags: bus master, medium devsel, latency 32, IRQ 169
        I/O ports at 1000 [size=32]
        Capabilities: <available only to root>

0000:05:04.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 08)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 32
        I/O ports at 1020 [size=8]
        Capabilities: <available only to root>

```

lsmod | grep snd
```
snd_emu10k1_synth       8448  0
snd_emux_synth         40448  1 snd_emu10k1_synth
snd_seq_virmidi         7552  1 snd_emux_synth
snd_seq_midi_emul       7424  1 snd_emux_synth
snd_seq_dummy           3972  0
snd_seq_oss            35712  0
snd_seq_midi           10400  0
snd_seq_midi_event      7552  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                58000  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           118180  5 snd_emu10k1_synth
snd_rawmidi            26784  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          8972  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_ac97_codec         92832  1 snd_emu10k1
snd_pcm_oss            61728  0
snd_mixer_oss          19456  1 snd_pcm_oss
snd_pcm                99080  4 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              26500  4 snd_seq,snd_emu10k1,snd_pcm
snd_ac97_bus            2304  1 snd_ac97_codec
snd_page_alloc         11272  2 snd_emu10k1,snd_pcm
snd_util_mem            5248  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9760  2 snd_emux_synth,snd_emu10k1
snd                    62956  25 snd_emu10k1_synth,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_util_mem,snd_hwdep
soundcore              10208  1 snd

```

---

### Post by mmtowns on 2006-12-27
I am having this same issue with my SB live.  I am booting from the Dapper LiveCD.

Have you had any luck?

---


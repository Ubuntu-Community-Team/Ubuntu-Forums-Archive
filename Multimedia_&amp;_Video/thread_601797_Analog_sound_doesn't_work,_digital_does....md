---
title: "Analog sound doesn't work, digital does..."
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by verhage on 2007-11-03
I'm having strange sound problems here...

According to lspci, my sound card is (onboard on an ASUS M2NPV-VM motherboard):
 ```

Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
Subsystem: ASUSTeK Computer Inc. Unknown device 81cb
Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
Capabilities: [44] Power Management version 2
Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
Capabilities: [6c] HyperTransport: MSI Mapping

```

No errors in dmesg, aplay -l says:
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Drivers are loaded correctly according to lsmod:
```

snd_hda_intel          24224  3
snd_hda_codec         262528  1 snd_hda_intel
snd_pcm_oss            49408  0
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           5380  0
snd_seq_oss            36608  0
snd_seq_midi           11008  0
snd_mpu401             11560  0
snd_mpu401_uart        10752  1 snd_mpu401
snd_rawmidi            29696  2 snd_seq_midi,snd_mpu401_uart
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  3 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    68904  16 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
snd_page_alloc         11792  2 snd_hda_intel,snd_pcm

```

But the strangest thing: I am able to play videos with AC3 audio streams through my video player (Xine). However, I'm not getting any sound of videos (or just plain audio files like mp3's) with an analog sound stream.

Does this problem seem familiar to anyone?

Can't remember any relating changes to my system. One minute it worked, it was broken the next...

---


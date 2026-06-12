---
title: "Sound works in single application"
date: 2007-09-14
forum: Multimedia &amp; Video
---

### Post by supradave on 2007-09-14
I just installed a new MB, a Gigabyte P35-DS3R with some form of integrated Intel sound hardware.  

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

lspci -v
00:1b.0 Audio device: Intel Corporation Unknown device 293e (rev 02)
        Subsystem: Giga-byte Technology Unknown device a002
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at f9100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

---

lsmod |  grep snd
snd_hda_intel          22040  2
snd_hda_codec         204800  1 snd_hda_intel
snd_pcm_oss            44416  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52464  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    53892  14 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         11016  2 snd_hda_intel,snd_pcm


Sound works fine if an application grabs hold of it.  Other application's sound doesn't work.  For example, starting a YouTube video will grab the sound system and not release it until I shut down Firefox or close the tab and wait some time.  Some buffered sounds, such as the console beeps will play at release, but then I'm stuck in the same situation of having an application grab hold of the sound system and not releasing it for some time.   It appears that some sort of multiplexing code needs to be turn on.

Any ideas?

Thanks,
Dave

---


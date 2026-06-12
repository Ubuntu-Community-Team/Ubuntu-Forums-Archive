---
title: "No sound devices found"
date: 2010-02-25
forum: Multimedia Software
---

### Post by mfraser on 2010-02-25
Up until about a week ago using Kubuntu 9.10, the sound on this computer was fine, but now every day when I turn the computer on I have no sound and I get a notification from Phonon saying:
The audio playback device NVidia (ALC883) does not work.
Falling back to.

If I turn the computer off and then back on, sound is working again.

lspci -v
Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
Subsystem: Giga-byte Technology Device a002
Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
Memory at ee100000 (32-bit, non-prefetchable) [size=16K]
Capabilities: [44] Power Management version 2
Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
Capabilities: [6c] HyperTransport: MSI Mapping Enable- Fixed+     
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


The only difference I can see from sound working and not working is in the response to lsmod |grep snd. When it is working I get:
snd_hda_intel        26920  4
snd_pcm              75296  5 snd_hda_intel,snd_hda_codec,cx88_alsa,snd_pcm_oss
snd_timer            22276  3 snd_pcm,snd_seq
snd                  59204  22 snd_hda_codec_realtek, snd_hda_intel, snd_hda_codec, snd_hwdep, cx88_alsa, snd_seq_oss, snd_pcm_oss, snd_mixer_oss, snd_pcm, snd_rawmidi, snd_seq, snd_timer, snd_seq_device

And when it isn't:
snd_hda_intel          26920  1
snd_pcm                75296  4  snd_hda_intel,snd_hda_codec,cx88_alsa,snd_pcm_oss
snd_timer              22276  2 snd_pcm,snd_seq
snd                    59204  18 snd_hda_codec_realtek, snd_hda_intel, snd_hda_codec, snd_hwdep, snd_seq_oss, snd_rawmidi, cx88_alsa, snd_pcm_oss, snd_mixer_oss, snd_pcm, snd_seq, snd_timer, snd_seq_device

---

### Post by mörgæs on 2010-02-25
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

---


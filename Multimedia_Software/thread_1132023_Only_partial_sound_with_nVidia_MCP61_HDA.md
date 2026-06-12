---
title: "Only partial sound with nVidia MCP61 HDA"
date: 2009-04-21
forum: Multimedia Software
---

### Post by ubergrog on 2009-04-21
Hi all. Just jumped over to the ubuntu distro & I have to say I'm pretty impressed so far. Installed the Kubuntu AMD64 Desktop Jaunty (9.04) RC on my Athlon & all's gone well except that I only get partial sound working. When I say partial the system plays the startup tune when I log in & I get sound when I test the "HDA NVidia (ACL888 Analog)" entry in the Mutlimedia settings (where the Digital & PulseAudio entries do not work), but I don't get any sound from any multimedia apps like mplayer or Amarok.

Here's the relevant entry from 'sudo lspci -v':

```
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Device 7309
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at febf4000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
        Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
```

and 'lsmod | grep snd' shows a lot of different modules:

```
snd_hda_intel         557364  3
snd_bt87x              23844  2
snd_pcm_oss            52352  0
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  3 snd_hda_intel,snd_bt87x,snd_pcm_oss
snd_seq_dummy          11524  0
snd_seq_oss            41984  0
snd_seq_midi           15744  0
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78792  20 snd_hda_intel,snd_bt87x,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  3 snd_hda_intel,snd_bt87x,snd_pcm
```

I've read some of the _[Comprehensive Sound Problem Solutions Guide](http://ubuntuforums.org/showthread.php?t=205449)_ (it's now 144 pages!!) & tried a few tips from _[here](http://ubuntuforums.org/showpost.php?p=6149347&postcount=51)_ & _[here](http://ubuntuforums.org/showthread.php?t=866965)_, but nothings worked so far. I've checked via alsamixer & don't see anything muted. About the only 'fix' I've knowingly left in place is adding my username to the audio group. Other than that I should be back to scratch.

Any help with this issue would be greatly appreciated. TX

---

### Post by ubergrog on 2009-04-23
Anybody?

---


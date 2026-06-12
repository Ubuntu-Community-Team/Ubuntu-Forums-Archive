---
title: "No Sound Blaster Live in 9.10"
date: 2009-12-17
forum: Multimedia Software
---

### Post by badcherry on 2009-12-17
I recently upgraded from 9.04 to 9.10 and my sound card worked just fine in 9.04, but it doesn't work in 9.10.  All of the correct emu10k1 modules appear to be loaded.

```
$ lsmod | grep snd
snd_seq_dummy          10756  0 
snd_emu10k1_synth      14336  0 
snd_emux_synth         40832  1 snd_emu10k1_synth
snd_seq_virmidi        13440  1 snd_emux_synth
snd_seq_midi_emul      14592  1 snd_emux_synth
snd_emu10k1           144288  1 snd_emu10k1_synth
snd_ac97_codec        112292  1 snd_emu10k1
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16904  2 snd_emu10k1,snd_pcm
snd_util_mem           12288  2 snd_emux_synth,snd_emu10k1
snd_hwdep              15108  2 snd_emux_synth,snd_emu10k1
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     15104  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                56880  9 snd_seq_dummy,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14988  8 snd_seq_dummy,snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  13 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd

```

It shows up here:
```
$ lspci | grep audio
00:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)

```

Running gnome-device-manager also shows that the sound card is present.  I am also a member of the audio group so that isn't the problem either.  When I goto System > Preferences > Sound > Hardware there are no devices listed.  And here is the output of some alsa commands.

```
$ aplay -l
aplay: device_list:223: no soundcards found...

$ alsamixer 

alsamixer: function snd_ctl_open failed for default: No such file or directory

```

Does anyone have any other ideas of places that I should look or other things I should try to get this working?

---


---
title: "Audigy 1 4.1?"
date: 2007-04-16
forum: Multimedia &amp; Video
---

### Post by volksman on 2007-04-16
Hey All!

Got a problem with one of my Ubuntu boxes.  It won't spit out 4.1 sound out of an Audigy 1 card.  I only get 2 channel stereo.

I've looked around for a fix but a lot of people say this works out of the box...This is a fresh install of Edgy with all the current patches up to last thursday or so.

Any suggestions?  I've not had to deal with sound issues in Ubuntu before so I'm not really sure where to start!

Thanks!

---

### Post by metnik on 2007-04-16
is your card supported? [http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix)

do u have, emu10k1 loaded?

---

### Post by volksman on 2007-04-16
I have a plain jane Audigy first gen...not sure of the exact model but I would be shocked if its not supported....plus the ALSA mixer gui does report an Audigy....

snd_emu10k1_synth       8960  0
snd_emux_synth         39296  1 snd_emu10k1_synth
snd_seq_virmidi         8576  1 snd_emux_synth
snd_seq_midi_emul       8192  1 snd_emux_synth
snd_seq                59120  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           128288  2 snd_emu10k1_synth
snd_rawmidi            27264  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec         97696  1 snd_emu10k1
snd_pcm                84612  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_seq_device          9868  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_timer              25348  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         11400  2 snd_emu10k1,snd_pcm
snd_util_mem            6016  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10756  2 snd_emux_synth,snd_emu10k1
snd                    58372  15 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
emu10k1_gp              4992  0
gameport               17160  2 emu10k1_gp

---

### Post by volksman on 2007-04-16
Problem solved.  alsmixergui played around with some of the levels and found the rear channels.  They are up now...

---


---
title: "Sound Problems with Audigy 4"
date: 2006-08-10
forum: Multimedia &amp; Video
---

### Post by zzneonzz on 2006-08-10
Hey first off i want to say these forums are awsome i have found much needed information. For a n00b like myself

Now on to my problems.

1. Only 1 application is able to do sound playback at any given time. I'm a gamer and when playing a game through wine and trying to hear in teamspeak i'm unable to do so it uses whichever was loaded first.  Can this be changed?

2. Mic doesn't seem to function very well with the +20DB Boost enabled in Alsamixer and the volume turned all the way up no one can hear me, i can't record anything, and i get feedback.  Any suggestions on this?

All help is greatly apreciated and so far you guys have been a great source of information.

---

### Post by simonn on 2006-08-10
Do you have an internal sound card as well as the Audigy?

See [http://ubuntuforums.org/showthread.php?p=1361856#post1361856](http://ubuntuforums.org/showthread.php?p=1361856#post1361856)

---

### Post by zzneonzz on 2006-08-10
Yes i do have an Intel HD Audio onboard soundcard but it is disabled in the bios.


zzneonzz@zzneonzz-desktop:~$ sudo lsmod | grep snd-*
snd_emu10k1_synth       7296  0
snd_emux_synth         37376  1 snd_emu10k1_synth
snd_seq_virmidi         7680  1 snd_emux_synth
snd_seq_midi_emul       7168  1 snd_emux_synth
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                51984  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           117156  2 snd_emu10k1_synth
snd_rawmidi            25504  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec         92704  1 snd_emu10k1
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_seq_device          8716  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_timer              25220  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10632  2 snd_emu10k1,snd_pcm
snd_util_mem            4608  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9376  2 snd_emux_synth,snd_emu10k1
snd                    55268  15 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
soundcore              10208  1 snd

---


---
title: "Choppy sound on new PC with Edgy"
date: 2007-02-07
forum: Multimedia &amp; Video
---

### Post by tribunal on 2007-02-07
Hello!
After buying new PC and installing Kubuntu Edgy Eft on it, sound worked fine 
But yesterday I decided to play one of ported games. As other ported games, it wants to use OSS. So, I had to disable KDE - sound - system. After this sound started to work in game, but it is so bad and choppy :( 
Everything was ok on my last PC with Dapper.
Sound card is onboard one.
This is a part of "lsmod", connected with sound:
snd_hda_intel          20116  2
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_mixer_oss          19584  1 snd_pcm_oss
snd_seq_dummy           4996  0
snd_seq_oss            36480  0
snd_seq_midi            9984  0
snd_rawmidi            27264  1 snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25348  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

---


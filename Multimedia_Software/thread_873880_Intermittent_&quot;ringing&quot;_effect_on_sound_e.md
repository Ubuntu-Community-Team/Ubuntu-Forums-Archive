---
title: "Intermittent &quot;ringing&quot; effect on sound events"
date: 2008-07-29
forum: Multimedia Software
---

### Post by torquill on 2008-07-29
Sound works fine, for the most part.  However, when a sound event is played, about half the time the right speaker has a high-frequency ringing effect.  It happens with the native laptop speakers and headphones as well.

If I play another sound, or stop and re-start playback of a DVD, sometimes it goes away.  Sometimes it doesn't, and may persist to the point that I give up and try again later.  I have no idea where to start looking for the source of the issue... suggestions?

Currently running Hardy on a Compaq Presario 700-CTO laptop.  Sound modules loaded:

```
luna@markanav:~$ lsmod | grep snd
snd_hda_intel         344728  2 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
```

Let me know if you need anything else.  Thanks!

---


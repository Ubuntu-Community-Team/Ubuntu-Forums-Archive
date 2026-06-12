---
title: "Main does not control volume on PCM channel"
date: 2009-03-30
forum: Multimedia Software
---

### Post by jkugler on 2009-03-30
Hello, I have a Dell Inspiron E1705 with Hardy (8.04) installed. Everything works: suspend, hibernate, wireless, fglrx, etc.  

However, the sound has one quirk: In the mixer, the Master volume control does not affect the PCM volume.  That is, if I mute sound, it does not mute PCM, if I turn down the main control, it does not turn down the PCM sound, until the Main volume is *all* the way down, then the PCM mutes out too.  I have to explicitly turn up and down the PCM channel.  Since most sound is PCM (even CD's that are read digitally), this is really annoying, especially since my volume keys (up, down, mute) do work and do control Main correctly.

The above symptoms are exhibited as well with the command-line alsa mixer.

```
$ lsmod|grep snd
snd_hda_intel         346136  11
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  5 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  5 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  27 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
```

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

```


Any ideas?

---


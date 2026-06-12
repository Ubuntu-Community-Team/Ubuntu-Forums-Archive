---
title: "Toshiba Satellite A75-S266 no sound on gusty"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by samblack on 2008-02-02
Greetings!

I've been working on trying to get sound working on a satellite A75-S266 for a few weeks now  to no avail.

I'm a professional linux administrator and programmer but I'm certainly no hardware genius. I'm hoping that someone here can shed some light on this subject.

I've researched the heck out of this problem on this and various other forums and through the internet at large. I've tried everything mentioned including building the latest alsa modules by hand, grub boot parameters, and various other hacks. Nothing has worked.

Anytime you load/reload the snd_atiixp module the message log (and dmesg) is filled with the following messages:
```
ALSA atiixp.c:434: atiixp: codec acquire timeout
[repeats a ridiculous amount of times]
ALSA ac97_codec.c:2061: AC'97 2 does not respond - RESET
```

Sound Device information:
```
 lspci | grep audio
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller

```

Kernel Module information:
```
lsmod | grep snd
snd_atiixp             21644  0 
snd_seq_dummy           4996  0 
snd_seq_oss            35456  0 
snd_seq_midi            9728  0 
snd_rawmidi            26112  1 snd_seq_midi
snd_seq_midi_event      8704  2 snd_seq_oss,snd_seq_midi
snd_atiixp_modem       17800  0 
snd_ac97_codec        101924  2 snd_atiixp,snd_atiixp_modem
snd_seq                54256  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ac97_bus                3456  1 snd_ac97_codec
snd_pcm_oss            43008  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                80644  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
snd_seq_device          9740  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              24580  2 snd_seq,snd_pcm
snd                    56708  12 snd_atiixp,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_atiixp_modem,snd_ac97_codec,snd_seq,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer
soundcore               8800  1 snd
snd_page_alloc         11656  3 snd_atiixp,snd_atiixp_modem,snd_pcm

```

I greatly appreciate any help anyone can provide.

---

### Post by Koorva on 2008-03-03
please let me know if you were able to fix this I don't have sound on my a75 either.

---

### Post by JackInBottle on 2008-03-03
I did not got sound card work on A75 with live CD, but after installation and did patch update, the sound card worked.

---


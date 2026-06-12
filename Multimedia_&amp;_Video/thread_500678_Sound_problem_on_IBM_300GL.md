---
title: "Sound problem on IBM 300GL"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by chris28 on 2007-07-14
Hi,

I've made a minimal installation on old IBM PC300GL and i've a strange problem with sound.

When i start computer i've no sound. If i test it with "Preferences"-"Sound" i've no error but no sound. But if I restart computer all sounds work fine after a simply test on sound preferences (but don't work before the test and specially the music when session is open).

And any time i stop completely (hard boot) the computer's sound don't work.

Do you think is it an harware problem. I've not tried to recompile alsa driver, do you think it could resolve my problem ? 

Here are some tests :

aplay -l

```
**** Liste des PLAYBACK périphériques ****
carte  0: PCI [ESS Allegro PCI], périphérique 0 : Allegro [Allegro]
  Sous-périphériques: 2/2
  Sous-périphérique: #0: subdevice #0
  Sous-périphérique: #1: subdevice #1
```

alsamixer


```
Card: ESS Allegro PCI                                                          &#9474;
&#9474; Chip: ESS Technology ESS1988                                                 &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-4.50, -4.50]                                          &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;    &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;      &#9474;    &#9474;     &#9474;       &#9474;      &#9474;     &#9474;      &#9474;     &#9474;     &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;     &#9474;       &#9474;      &#9474;     &#9474;      &#9474;     &#9474;     &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#9474;      &#9474;     &#9474;      &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#9474;      &#9474;     &#9474;      &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#9474;      &#9474;     &#9474;      &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#9474;      &#9474;     &#9474;      &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#9474;      &#9474;     &#9474;      &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#9474;      &#9474;     &#9474;      &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#9474;      &#9474;     &#9474;      &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#9474;      &#9474;     &#9474;      &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#9474;      &#9474;     &#9474;      &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9474;
&#9474;    &#9474;OO&#9474;     &#9474;OO&#9474;                        &#9474;OO&#9474;      &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;                        &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;   90<>90     81         0        0     81<>81     0<>0    81<>81      0      &#9474;
&#9474; < Master >Master M  3D Contr 3D Contr   PCM       Line      CD      Mic      
```


```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
snd-maestro3
```

lsmod|grep snd

```

snd_maestro3           27012  1 
snd_ac97_codec         98336  1 snd_maestro3
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  1 snd_pcm
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
```

Thanks

---


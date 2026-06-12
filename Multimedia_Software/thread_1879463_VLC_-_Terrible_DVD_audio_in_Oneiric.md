---
title: "VLC - Terrible DVD audio in Oneiric"
date: 2011-11-11
forum: Multimedia Software
---

### Post by wwwookie on 2011-11-11
Hi - I recently installed oneiric and things were going fine until I tried to play a DVD with VLC, the sound was terrible! It sounds like somebody's got an effects unit and turned the reverb and delay way too high - so much distortion that words are unintelligible and with regular beats, about 3 per second. I tried again with on clean install, and got the same results. This problem does not exist in Natty or earlier.

Are other people finding the same problem? And if so, is there a fix?

Here are some details:

```
$ lspci | grep Multimedia
00:06.0 Multimedia audio controller: Yamaha Corporation YMF-724 (rev 05)
$ lsmod | grep snd
snd_ymfpci             34301  2 
gameport               15060  1 snd_ymfpci
snd_ac97_codec        106082  1 snd_ymfpci
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_ymfpci,snd_ac97_codec
snd_opl3_lib           18863  1 snd_ymfpci
snd_hwdep              13276  1 snd_opl3_lib
snd_page_alloc         14115  2 snd_ymfpci,snd_pcm
snd_mpu401_uart        13865  1 snd_ymfpci
snd_seq_midi           13132  0 
snd_rawmidi            25241  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  4 snd_ymfpci,snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device         14172  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  14 snd_ymfpci,snd_ac97_codec,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
```My fix so far is to keep using natty, I have already learned the hard  way not to upgrade a perfectly working distribution - you can't go back.  It's always better to put a new release on a separate partition and  test it until you are sure it works properly!

---

### Post by anquetil.n on 2011-12-18
I believe I had a similar problem

If you did not solved you problem
go in system settings >> Multimedia >> phonon
and in Audio Hardware setup choose Analogue stereo output instead of analogue surround

For me it solved the problem, sound is now very good.

Only problem is that I didn't find out how to have both audio output and input :-(
On my machine (macbook), I have to chosse one or the other.

If anybody knows how to solve that I would wellcome some ideas....

---


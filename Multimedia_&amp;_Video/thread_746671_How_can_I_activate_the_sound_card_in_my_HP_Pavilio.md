---
title: "How can I activate the sound card in my HP Pavilion DV 6799ef?"
date: 2008-04-05
forum: Multimedia &amp; Video
---

### Post by Arrachecoeurs on 2008-04-05
Hello!
I am brand new to Linux. I have installed ubuntu in my HP Pavilion Dv 6799 ef and I cannot get any sound. 
How can I fix this? Could anyone let me some help? Thanks.

---

### Post by warp99 on 2008-04-05
Open a terminal and type the following:
```
lspci -v |grep Audio
```
then:
```
lsmod |grep snd
```
and post the results to this thread.

---

### Post by TroyDowling on 2008-04-06
I have an HP Pavilion DV9013ca. Is the process universal to the laptop family? I'm currently running the Beta for Hardy.

---

### Post by Arrachecoeurs on 2008-04-16
Thank you for the answers!
I could finally make it!

Arrachecoeurs

---

### Post by Arrachecoeurs on 2008-04-24
mordi@Orestes:~$ lspci -v |grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
mordi@Orestes:~$ lsmod |grep snd
snd_hda_intel         344728  3 
snd_hwdep              10500  1 snd_hda_intel
snd_pcm_oss            42144  0 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_mixer_oss          17920  1 snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_hda_intel,snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
mordi@Orestes:~$ 

these are the results... I updated to 8.04 and there is no longer sound...

---


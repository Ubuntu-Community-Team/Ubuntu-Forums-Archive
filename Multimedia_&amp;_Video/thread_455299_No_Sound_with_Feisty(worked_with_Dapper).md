---
title: "No Sound with Feisty(worked with Dapper)"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by littleiffel on 2007-05-26
Hi There, I have upgraded to Feisty recently. Everything worked fine, except for Sound. Sound used to work perfect(always) under Dapper. Now under Feisty Sound worked only once in a while, trying to fix this as described in [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto), now sound does not work at all anymore.

I have a Thinkpad x60 with an Intel Sound Card
lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)

Modules are loaded too

 lsmod |grep sn
snd_hda_intel         244632  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                81028  2 snd_hda_intel,snd_pcm_oss
snd_seq_oss            35200  0 
snd_seq_midi_event      8576  1 snd_seq_oss
snd_seq                54000  4 snd_seq_oss,snd_seq_midi_event
snd_timer              24196  2 snd_pcm,snd_seq
snd_seq_device          9612  2 snd_seq_oss,snd_seq
snd                    56324  10 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm


I have no clue what's wrong?Is there somebody out there experiencing similar problems or somebody knowing how to solve this isue?

Thanks in advance

---

### Post by rrwo on 2007-05-28
I have the same problem. Here's something to check: does the sound consistent work with a cold boot (when the computer is off) but not work when from a warm boot/restart or wake up from hibernate?

---

### Post by irezumi_x on 2007-05-28
I have this problem also, NO sound at all since upgrading to 7.04

---

### Post by lexarrow on 2007-05-28
Try unplugging the AC cable and give it a restart

---

### Post by irezumi_x on 2007-05-28
this solution i found on a board somewhere seems to work partially:

1. edit alsa-base:
sudo gedit /etc/modprobe.d/alsa-base

2. add this line to the end of that file:
options snd-hda-intel model=3stack

3. save & close the file

4. restart

it has the sound working again for me, but only one channel i think, and nothing on the headphones..

---


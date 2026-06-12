---
title: "Realtek ALC260 configured but no sound"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by lbort on 2006-11-11
Hi,

A few months ago, I installed Ubuntu 6.10 on my laptop. Since then I have a problem with my sound card. It seems to be correctly installed. I can play music but no sound.

Following are the details of my configuration:

$ uname -a
Linux linox **2.6.15-27-686** #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux

$ lspci | grep Audio
0000:00:1b.0 0403: Intel Corporation 82801G (**ICH7** Family) High Definition Audio Controller (rev 02)

$ cat /proc/asound/version
**Advanced Linux Sound Architecture Driver Version 1.0.13**.
Compiled on Nov 11 2006 for kernel 2.6.15-27-686 (SMP).

$ cat /proc/asound/cards
 0 [Intel          ]: **HDA-Intel** - HDA Intel
                      HDA Intel at 0x6c340000 irq 58

$ cat /proc/asound/card0/codec#0 | grep Codec
Codec: **Realtek** **ALC260**

$ lsmod | grep snd
snd_hda_intel          22136  5
snd_hda_codec         175312  1 snd_hda_intel
snd_pcm_oss            49728  0
snd_mixer_oss          20000  2 snd_pcm_oss
snd_pcm                88420  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26660  2 snd_pcm
snd                    62084  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  2 snd
snd_page_alloc         11336  2 snd_hda_intel,snd_pcm

Alsamixer shows everything on maximum and unmuted. Sound is not muted, I have used kmix to unmute it, but still no sound.

I have download the latest stable release directly from alsa but still no sound.

The strange thing is that when I play something I can hear it on my headphones but the sound is very low. It is difficult to hear.

Anybody with the same problem?

Thanks in advance,
Lino

---

### Post by lbort on 2006-11-22
Hi,

Is anyone monitorizing this thread? More than 100 people have viewed this thread, probably because they have the same problem.

I don't kwow whether this is the correct place to post this kind of problems. If this is not the correct place, can anyone tell me which is it? I am using Ubuntu for two years at home and work but I have the problem described in this thread with my new laptop.

Thanks in advance,
Lino

---

### Post by MadeR on 2006-12-24
same problem here with a travelmate c200

---

### Post by MadeR on 2007-01-01
[http://ubuntuforums.org/showthread.php?t=324764&highlight=alc260](http://ubuntuforums.org/showthread.php?t=324764&highlight=alc260)

---

### Post by mkent91 on 2007-01-01
try selecting "autodetect" instead of selecting Realtek ALC260 that should solve your problem of no sound. If not then I'm very sorry and I don't know what the sound problem is.

---


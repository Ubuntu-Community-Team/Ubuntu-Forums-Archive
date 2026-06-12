---
title: "Intel ICH sound cards"
date: 2005-12-24
forum: Multimedia &amp; Video
---

### Post by asker_student on 2005-12-24
Dear all;
   I am somewhat new to Ubuntu. My problem is my Intel ICH sound card (in a Presarion 2800 Laptop). The system does produce sounds as alerts but no player works.

$plaympeg 1.mp3 
Warning: Couldn't init SDL audio: No available audio device
Will ignore audio stream

some howtos on the web instructed to load i810_audio.ko  but:

# insmod i810_audio.ko
insmod: error inserting 'i810_audio.ko': -1 Unknown symbol in module

and lsmod | grep intel reveals:

snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

my sound device in Volume Control is "Intel 82801CA-ICH3"  and changing it to Analog Devices (OSS mixer) does not change anything.

Other Information:

# cat /proc/asound/card0/intel8x0
Intel8x0

Global control        : 0x00000002
Global status         : 0x00300100
AC'97 codecs ready    : primary

What can I do to become able to play sound?

Sincerely Yours,
Asker.

---


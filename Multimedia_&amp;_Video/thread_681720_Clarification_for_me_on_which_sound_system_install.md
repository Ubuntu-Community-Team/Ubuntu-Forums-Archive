---
title: "Clarification for me on which sound system installed default"
date: 2008-01-29
forum: Multimedia &amp; Video
---

### Post by LinChapulin on 2008-01-29
I have Gutsy 7.10 installed. I am trying to figure out a problem I am having with Audacity barely recording streamed audio from firefox. If I am reading the output correctly it is using OSS? I looked and alsa-base is installed as well...I also saw that there is a wrapper available for ALSA that has to do with getting apps using ALSA to work when using OSS...can someone help me understand better what is going on here?

Thanks,

LinChapulin

Laptop is a Fujitsu Lifebook N Series (N6460)
lspci shows:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

cat /proc/asound/cards

0 [Intel ]: HDA-Intel - HDA Intel
HDA Intel at 0xfe500000 irq 23

lsmod:

snd_hda_intel 263712 1 
snd_pcm_oss 44672 0 
snd_mixer_oss 17664 1 snd_pcm_oss
snd_pcm 80388 2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy 4740 0 
snd_seq_oss 33152 0 
snd_seq_midi 9600 0 
snd_rawmidi 25728 1 snd_seq_midi
snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi

snd_seq 53232 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 24324 2 snd_pcm,snd_seq
snd_seq_device 9228 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seqLinChapulin 
  
Posts: 1
Joined: Tue Jan 29, 2008 5:34 am 
Private message

---


---
title: "Fresh Ubuntu x64 Installation, There's a sound problem."
date: 2009-01-11
forum: Multimedia Software
---

### Post by ricardo072 on 2009-01-11
Hi all,

I have a fresh installation of Ubuntu WorkStation x64 ( minor hw details: Intel core 2 Cuad, NVidia GeForce 8600GT video card, 8 Gb ram and motherboard gigabyte GA-EP35-DS3L ) I already installed the NVidia video driver ver 177 and the first updates were installed (more than 200)...

This is the problem, my motherboard have a 7.1 sound channels output integrated, I have some questions:

1) How can I configure the sound in ubuntu ? Currently, I can only hear an 2.1 output sound, and to be honest I don't know how configure my sound. Hope this helps:

richard@WorkStation-Home:~$ lspci
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

richard@WorkStation-Home:~$ lsmod
Module                  Size  Used by
snd_hda_intel         489264  3 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                51612  0 
snd                    79432  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm

Your help is very appreciated.
Thanks a lot.
Best regards.

---


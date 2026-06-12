---
title: "lost all sound"
date: 2008-08-07
forum: Multimedia Software
---

### Post by tonymoloney on 2008-08-07
I've suddenly lost all sound on my Lenovo laptop. Its been working fine up until today.
Here's the output from lsmod | grep snd :

tony@tony-laptop:~$ lsmod | grep snd
snd_hda_intel         263840  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

Is there anything else I need to look at?

---

### Post by loligager on 2008-08-07
are there any proprietart drivers
did the sound work before
What version of the distro are you on...
when and what [to the best of your knowledge] did you do before the problem occured
did u modify alsa in any way before and are you using pulse media

---

### Post by tonymoloney on 2008-08-08
No propriety drivers
sound has been working for the last twelve months
I'm on Gutsy Gibbon and have been for months
Didn't do anything before the sound stopped
Didn't modify alsa - not using pulse media as far as I know
Before the problem I was able to use VLC, play CDs, play Utube clips and even play midi files and I've had Band in a Box working in WINE for some months.

---


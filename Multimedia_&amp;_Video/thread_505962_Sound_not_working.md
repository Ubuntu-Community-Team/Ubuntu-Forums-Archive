---
title: "Sound not working"
date: 2007-07-21
forum: Multimedia &amp; Video
---

### Post by subaruwrx on 2007-07-21
Hi,

Installed ubuntu feisty onto my Compaq V3136TU notebook but sound does not work.

> collinyeo@collinyeo-laptop:~$ lspci |grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

collinyeo@collinyeo-laptop:~$ lsmod|grep snd
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm



Tried adding "options snd-hda-intel" to /etc/modprobe.d/alsa-base but to no avail.

Any idea why?

Fedora and Opensuse works out of the box but I really like Ubuntu. :(

---

### Post by fredj on 2007-07-21
The line you have added to alsa base won't do anything.
Try adding 
options snd-hda-intel position_fix=1 model=3stack
Also open the Alsa mixer (double click on the speaker icon in the taskbar). Go to the Edit->Preferences
menu and add all the volume controls for playback and mixing (and all the switches) and make sure that
they are not muted and have suitable volume levels.
If you are still having problems then open a terminal and type
sudo cat /proc/asound/card0/codec\#*
Post the output from that here.

---

### Post by subaruwrx on 2007-07-21
> **fredj said:**
> The line you have added to alsa base won't do anything.
Try adding 
options snd-hda-intel position_fix=1 model=3stack
Also open the Alsa mixer (double click on the speaker icon in the taskbar). Go to the Edit->Preferences
menu and add all the volume controls for playback and mixing (and all the switches) and make sure that
they are not muted and have suitable volume levels.
If you are still having problems then open a terminal and type
sudo cat /proc/asound/card0/codec\#*
Post the output from that here.

sheesh it works!!! its the PCM-2 that is muted.

Thanks so much!

---

### Post by fredj on 2007-07-22
Good, well done!

---


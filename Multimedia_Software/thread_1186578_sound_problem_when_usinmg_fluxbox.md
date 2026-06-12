---
title: "sound problem when usinmg fluxbox"
date: 2009-06-13
forum: Multimedia Software
---

### Post by 4dplane on 2009-06-13
Hi,

I am on an Intel motherboard(DG45FC) with a Intel 82801JR (ICH10R) sound card with Ubuntu 9.04 and Kernel 2.6.28-11-generic.

Here is lsmod | grep snd

```
snd_hda_codec_intelhdmi    20608  1
snd_hda_codec_idt      65548  1
snd_hda_intel          34120  3
snd_hda_codec          83584  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              15364  1 snd_hda_codec
snd_pcm_oss            45984  0
snd_mixer_oss          22912  1 snd_pcm_oss
snd_pcm                82948  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy          10884  0
snd_seq_oss            36224  0
snd_seq_midi           14240  0
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57584  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29192  2 snd_pcm,snd_seq
snd_seq_device         15372  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    66852  19 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         17032  2 snd_hda_intel,snd_pcm
```

Here is cat /proc/asound/modules
 ```
0 snd_hda_intel
```

When I am logged into a regular account(non-Fluxbox) sounds works perfectly in all application like Firefox, Flash VLC etc ... but the moment I log into the fluxbox account there is no sound except in gnome-sound-properties panel when I select oss analog and hit test, there is sound, but no where else!!!](*,)

The sound-settings-properties when logged into the non-Fluxbox account are all set to ALSA and everything works but if I set that in the Fluxbox account there is no sound including the test sound.

I have made sure in alsamixer nothing is muted and all volumes are turned up. And I have tried all the audio output ports on the sound card. 

Also, in the non-Fluxbox account the master volume does not do change the volume, the PCM channel does. why?

Thanks for any help,

This makes me think I need to load something in the start up script for Fluxbox but I do not know what.

---


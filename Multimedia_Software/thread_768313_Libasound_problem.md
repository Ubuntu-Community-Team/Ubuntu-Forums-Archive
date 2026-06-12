---
title: "Libasound problem"
date: 2008-04-26
forum: Multimedia Software
---

### Post by hallvor1 on 2008-04-26
On a thinkpad t61, with a intel hda ad1984 card I have a problem with sound. It's running hardy just upgraded yesterday. Since this card was not supported with old alsa sound has never worked on this machine. But in hardy it should work. Has anybody seen this before:

```
hallvor@thinkpad:~$ aplay -L
aplay: relocation error: aplay: symbol snd_device_name_hint, version ALSA_0.9 not defined in file libasound.so.2 with link time reference

```
If I try to play something in aplay I get this:

```
hallvor@thinkpad:~$ aplay /usr/share/hwdb-client/sound.wav
ALSA lib pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
aplay: main:546: Feil i åpning av lyd: No such file or directory
```

I have tried purging and reinstalling libasound2, linux-sound-base, alsa-base and alsa-utils. Any other packages that are involved in this?

Any suggestions welcome.

Other relevant info:

```
hallvor@thinkpad:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
hallvor@thinkpad:~$ lsmod|grep snd
snd_hda_intel         344728  1
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
```

```
hallvor@thinkpad:~$ lspci |grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

---

### Post by hallvor1 on 2008-04-26
Fixed. Stupid thing, was old crap left over from an earlier attempt to fix sound on this box. If you ever starts installing alsa from source, make absolutely certain you get rid of everything again.

---


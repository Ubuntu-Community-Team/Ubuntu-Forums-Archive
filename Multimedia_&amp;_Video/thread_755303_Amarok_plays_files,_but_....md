---
title: "Amarok plays files, but ..."
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by Alibabac on 2008-04-14
there are no system sounds, jack hangs up, terminal window looks like this after some commands:
________________________________________________________________________
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 2: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
________________________________________________________________________
, but : 
________________________________________________________________________
 aplay -vv somefile.wav
ALSA lib confmisc.c:769:(parse_card) cannot find card ''
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:545: audio open error: No such device
_________________________________________________________________________
MB is asrock Nf3 chipset with integrated audio, 64 bit ubuntu. I wonder why are some USB cards listed, there are no USB sound cards on system ! any help ?

---


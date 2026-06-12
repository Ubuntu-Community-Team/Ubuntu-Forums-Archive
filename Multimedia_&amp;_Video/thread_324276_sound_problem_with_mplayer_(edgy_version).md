---
title: "sound problem with mplayer (edgy version)"
date: 2006-12-23
forum: Multimedia &amp; Video
---

### Post by fbarsoba on 2006-12-23
Hi,

I am having some problems with my laptop sound system.. I recently tried to configure logitech headset 350 and now i am having problems playing regular files. through the laptop speakers. Flash sound works fine in mozilla.. but no sound with the cnn videos, for instance. When trying to play a wav file i got the following:

> Audio file file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 11025 Hz, 2 ch, s16le, 24.0 kbit/6.80% (ratio: 3000->44100)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
alsa-lib: confmisc.c:670:(snd_func_card_driver) cannot find card 'Headset'
alsa-lib: conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
alsa-lib: confmisc.c:391:(snd_func_concat) error evaluating strings
alsa-lib: conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
alsa-lib: confmisc.c:1070:(snd_func_refer) error evaluating name
alsa-lib: conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
alsa-lib: conf.c:3947:(snd_config_expand) Evaluate error: No such device
alsa-lib: pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default
alsa-init: playback open error: No such device
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video


tnx,
Fernando

---


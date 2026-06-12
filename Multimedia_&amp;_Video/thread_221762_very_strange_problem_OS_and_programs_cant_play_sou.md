---
title: "very strange problem: OS and programs cant play sounds!"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by kitt on 2006-07-24
Ubuntu cant play sounds!

Hi everyone,
All of a sudden, ubuntu has stopped playing sounds- BUT..I am able to play the sound files i want..its just that no program (games, ubuntu, etc.) is able to play any sounds.
Everything was working perfectly out-of-the-box, but now i can only play the sound files in the media players. 

aplay returns this:
-------------------------------------------------------------------------
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card 'Audio'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:544: audio open error: No such device
-----------------------------------------------------------------------------

aplay -l returns:
-----------------------------------------------------------------------
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
------------------------------------------------------------------
And heres what alsamixer throws up:
alsamixer: function snd_ctl_open failed for default: No such device
------------------------------------------------------------------
My machine: acer aspire 5004

---

### Post by RedKrieg on 2006-08-01
Wow, I just started having the same issue with my nvidia onboard sound.  I never tried the sound before though, because I was using a usb headset, so it may never have worked.  Same exact errors though

---

### Post by RedKrieg on 2006-08-01
Whoops, think I fixed it.  I renamed my .asoundrc and .asoundrc.asoundconfig or whatever files (all the ones that started with .asound) to [filename].backup

when I logged out and back in, sound worked fine!

---


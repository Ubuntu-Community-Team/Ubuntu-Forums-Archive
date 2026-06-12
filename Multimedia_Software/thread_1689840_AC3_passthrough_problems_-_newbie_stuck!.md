---
title: "AC3 passthrough problems - newbie stuck!"
date: 2011-02-17
forum: Multimedia Software
---

### Post by pjm1 on 2011-02-17
I've done a search for solutions to this problem but am such an ubuntu newbie I'm struggling to work out whether other solutions will help me or collapse my system!

I have a Behringer UCA202 USB audio input/output device which supports optical out to my receiver and (supposedly) is linux compatible.  I am using it at the moment, with the optical out and I've managed to get it work relatively easily... sort of....

In that I can hear sounds, music etc.  But I cannot get any applications to passthrough AC3 or DTS - at best they downmix it to stereo or stay silent or output gibberish.  I've tried MPlayer, Movie Player, VLC, XBMC and Boxee and all will play sound but none play AC3/DTS from either files or DVDs.  I've messed around with a few simple commands to make sure it's recognised but am now stuck:

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```speaker-test -Dplug:surround51 -c6 -twav
```
speaker-test 1.0.22

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
ALSA lib pcm_params.c:2150:(snd1_pcm_hw_refine_slave) Slave PCM not usable
Broken configuration for playback: no configurations available: Invalid argument
Setting of hwparams failed: Invalid argument

```This latter one suggests to me that I need to fix a config file or something, but unsure how!

Any ideas, help and stuff would be most welcome - am a complete newbie to linux but am reasonably computer literate apart from that!

Thanks in advance.

---


---
title: "ALSA errors"
date: 2008-08-13
forum: Multimedia Software
---

### Post by LXXXIII on 2008-08-13
Hey, I've read the sticky and arrived at a simple conclusion: my soundcard that is an emu0202 usb is not yet well supported. But strangely, under Mint I do have sound while doing ordinary things like playing videos. It is just that, for example when I compile an SDL/C++ program to test, ALSA doesn't work when trying to run the program. Is there any way to get it to work so I can continue my programming?

Here is what's shown in the shell when executing the program:

```
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default

```I've troubleshooted it before, but I've been searching the internet, reading forums, checking the ALSA site, and you name it, but I haven't yet gotten good results. So you could understand I'm getting a bit impatient :(

Here is what's shown using **aplay** **-l**:
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: USB [E-MU 0202 | USB], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```And **lspci -v** doesn't show the card.

---


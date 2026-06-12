---
title: "UA-25 + Alsa, need help!"
date: 2008-04-20
forum: Multimedia &amp; Video
---

### Post by radivx on 2008-04-20
Hi,
I'm using a UA-25 USB device. The UA-25 device lacks of hardware mixing and I need some help configuring it with software mixing.

When I start programs like mocp and firefox I get these errors:

Trying ALSA...
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default

cat /proc/asound/cards:

 1 [UA25           ]: USB-Audio - UA-25
                      EDIROL UA-25 at usb-0000:00:0b.0-1, full speed

This might be the cause of the problem. If it tries to locate card 0 and UA-25 is assigned as card 1?

The Gnome programs like Totem and Rythmbox works like a charm (alone, and both running). The use of the oss wrapper /dev/dsp will usually make programs play sound, but it removes software mixing.
I'm running Hardy but this card has been troubled on all the ubuntu versions I've tested.

Please help me getting alsa working properly.

---


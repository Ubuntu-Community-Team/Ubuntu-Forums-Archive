---
title: "Can't get sound working on new Nvidia based Mac Mini"
date: 2009-06-01
forum: Multimedia Software
---

### Post by eisbaer128 on 2009-06-01
Hello,

I'm trying to get sound working on my new Nvidia based Mac Mini but somehow looks like I'm missing something ?

I'm using Ubuntu 9.04

I've added to

/etc/modprobe.d/alsa-base.conf

options snd-hda-intel model=imac24


I get the following output:

 /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0x93480000 irq 22


aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: NVidia [HDA NVidia], Gerät 0: ALC885 Analog [ALC885 Analog]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: NVidia [HDA NVidia], Gerät 1: ALC885 Digital [ALC885 Digital]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0

Which looks O.K. but:

alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

and:
play
ALSA lib confmisc.c:768:(parse_card) cannot find card 'Intel'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:608: Fehler beim Öffnen des Audiogerätes: No such device

Somehow looks like the card is not there or has the wrong configuration but I really have no idea what's missing.

---

### Post by eisbaer128 on 2009-06-01
Solved the problem on my own. Everything was setup correctly justed missed to specify the card number in the alsamixer and aplay calls.

---


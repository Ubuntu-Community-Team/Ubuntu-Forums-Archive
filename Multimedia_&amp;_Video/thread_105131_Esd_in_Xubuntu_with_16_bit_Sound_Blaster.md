---
title: "Esd in Xubuntu with 16 bit Sound Blaster"
date: 2005-12-17
forum: Multimedia &amp; Video
---

### Post by stuporglue on 2005-12-17
Hi, 

I installed Ubuntu in server mode, then installed xubuntu-desktop, plus a couple of Gnome apps that I wanted (Sound-juicer and Rhythmbox, plus their dependencies.) 

Rhythmbox, Sound-juicer and gnome-cd don't play any sound. 

The CD player cccd DOES play CDs just fine.

When I run gnome-cd from the command line, I get a continual output of:
```

No GConf default audio sink key and esdsink doesn't work
```

It seems that esd is probably the problem. 

When I try to run esd I get:

```
 ALSA lib confmisc.c:560:(snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:955:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3948:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM default
```


The card is a 16 bit sound blaster. I have these sound blaster modules loaded:
```
student@ubuntu:~$ lsmod | grep sb
usbcore               104316  2 uhci_hcd
sb                     12932  2
sb_lib                 42288  1 sb
uart401                11204  1 sb_lib
sound                  70444  4 sb_lib,uart401
soundcore               9184  4 sb_lib,sound
```


Any ideas what I can do to get gnome-cd and Rhythmbox working? 

Thank you.

---

### Post by stuporglue on 2005-12-17
I've gotten it sort of working by starting Gnome services along with Xfce4. 

It's choppy now, but working.

---


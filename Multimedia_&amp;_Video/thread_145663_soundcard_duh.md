---
title: "soundcard duh?"
date: 2006-03-16
forum: Multimedia &amp; Video
---

### Post by cryptidan on 2006-03-16
Tells me that another application is using the soundcard, how can this be solved?
Here ya go, in all its glory:
> root@oldmine:/tmp# modinfo snd-ens1371
filename:       /lib/modules/2.6.12-10-386/kernel/sound/pci/snd-ens1371.ko
author:         Jaroslav Kysela <perex@suse.cz>, Thomas Sailer <sailer@ife.ee.et hz.ch>
license:        GPL
description:    Ensoniq/Creative AudioPCI ES1371+
vermagic:       2.6.12-10-386 386 gcc-3.4
depends:        snd-pcm,snd-rawmidi,snd,gameport,snd-ac97-codec
alias:          pci:v00001274d00001371sv*sd*bc*sc*i*
alias:          pci:v00001274d00005880sv*sd*bc*sc*i*
alias:          pci:v00001102d00008938sv*sd*bc*sc*i*
srcversion:     D3D8CC5AD67BB5BCEE48E2D
parm:           joystick_port:Joystick port address. (array of int)
parm:           enable:Enable Ensoniq AudioPCI soundcard. (array of bool)
parm:           id:ID string for Ensoniq AudioPCI soundcard. (array of charp)
parm:           index:Index value for Ensoniq AudioPCI soundcard. (array of int)
root@oldmine:/tmp# /etc/modprobe.d/sound
bash: /etc/modprobe.d/sound: No such file or directory
root@oldmine:/tmp# cd /usr/share/sounds
root@oldmine:/usr/share/sounds# aplay xxx.wav
ALSA lib confmisc.c:560:(snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver return ed error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned er ror: No such file or directory
ALSA lib confmisc.c:955:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned err or: No such file or directory
ALSA lib conf.c:3948:(snd_config_expand) Evaluate error: No such file or directo ry
ALSA lib pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:533: audio open error: No such file or directory
root@oldmine:/usr/share/sounds#
root@oldmine:/usr/share/sounds# sudo fuser -v -m /dev/dsp
/dev/dsp: No such file or directory
root@oldmine:/usr/share/sounds# /etc/hotplug/blacklist
bash: /etc/hotplug/blacklist: Permission denied
root@oldmine:/usr/share/sounds# sudo modprobe es1371
root@oldmine:/usr/share/sounds# [/etc/modules] add 'ens1371'
bash: [/etc/modules]: No such file or directory
root@oldmine:/usr/share/sounds# [esd]
bash: [esd]: command not found
root@oldmine:/usr/share/sounds# /etc/asound.conf
bash: /etc/asound.conf: No such file or directory
root@oldmine:/usr/share/sounds# cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory
root@oldmine:/usr/share/sounds# ls -l /dev | grep dsp


as you can see, I have *no* idea of what I am doing....

---

### Post by FarEast on 2006-03-27
Hi cryptidan;) ,

```
root@oldmine:/usr/share/sounds# cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory
```

According to the response above, the system does not recognize your sound card. Do you know which one is on your system?  If it is on PCI bus, it will be shown by executing 'lspci | grep audio' from the command line.

---


---
title: "How can I activate spdif out?"
date: 2007-08-14
forum: Multimedia &amp; Video
---

### Post by fjf on 2007-08-14
I have gone through the posts about spdif issues, but found nothing that help.  I've played with the switches in the sound guys in gnome, and digital out gives no so sound.  There is no digital that I can see in alsamixer.  My aplay -l gives: 

**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC883 Analog [ALC883 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: ALC883 Digital [ALC883 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

I have no asound.conf file.  When I try to create it and add to the /ect/asound.conf the line:

pcm "hw:0,1"

I get the sound muted, and the aplay -l says now:

**** Lista de PLAYBACK Dispositivos Hardware ****
ALSA lib conf.c:974:(parse_value) pcm is not a string
ALSA lib conf.c:1587:(snd_config_load1) _toplevel_:1:12:Argumento inválido
ALSA lib conf.c:2848:(snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2712:(snd_config_hooks_call) function snd_config_hook_load returned error: Argumento inválido
ALSA lib conf.c:3075:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:231: control open (0): Argumento inválido

Any hints?.  Thanks!.

---

### Post by renzokuken on 2007-08-14
you have the same audio hardware as me. have you ever compiled / updated to the latest alsa-driver. thats what i had to do to get my sound working properly.

---

### Post by fjf on 2007-08-16
Dunno how to do that...finally I installed a chaintech av710 for music and is working fine...Thanks!.

---


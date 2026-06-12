---
title: "HELP! Last update killed my sound!"
date: 2009-10-10
forum: Multimedia Software
---

### Post by Huggy on 2009-10-10
The last update I did killed my sound! I rely very heavily on sound. Please anyone help me? I think I have pulse audio.

---

### Post by david.ptm56 on 2009-10-12
Same problem here. Restarted today and no sound at all. Also one IP asigned by dhcp changed to static in my iptables and flash is very unstable now... yeah, I'm so happy with my ubuntu... :roll:I should have installed free-bsd bu now I won't be able to change my SO for a while.

```
$ alsamixer
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused


alsamixer: function snd_ctl_open failed for default: Connection refused
```
```
$ qamix
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
Did not find any soundcard.
```
```
$ pulseaudio
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
E: alsa-util.c: Error opening PCM device hw:0,1: No existe el fichero ó directorio
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device=hw:0,1"): initialization failed.
E: main.c: Module load failed.
E: main.c: Fallo al intentar iniciar el demonio.
```

I hope somebody has any clue about this problem. Thank you very much guys.

---


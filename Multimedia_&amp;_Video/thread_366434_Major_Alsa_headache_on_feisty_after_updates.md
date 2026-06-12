---
title: "Major Alsa headache on feisty after updates"
date: 2007-02-20
forum: Multimedia &amp; Video
---

### Post by dtruesdale on 2007-02-20
After updates today the system no longer sees my options in alsa-base. and if I run alsamixer this is what I get:

ALSA lib conf.c:1587:(snd_config_load1) _toplevel_:3:11:Unexpected char
ALSA lib conf.c:2848:(snd_config_hook_load) /home/dtruesdale/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2712:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3075:(snd_config_update_r) hooks failed, removing configuration

alsamixer: function snd_ctl_open failed for default: Invalid argument

the modules are loaded alsa fails even with cedega test. Alsamixer runs under root. Anyone have any ideas? Permissions?

---

### Post by dtruesdale on 2007-02-20
Solved deleted /home/user/.asoundrc

---


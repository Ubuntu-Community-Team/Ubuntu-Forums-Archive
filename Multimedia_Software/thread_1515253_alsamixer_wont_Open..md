---
title: "alsamixer wont Open."
date: 2010-06-22
forum: Multimedia Software
---

### Post by KingOfDeath on 2010-06-22
When I Open Or Write alsamixer In the terminal this what shows up to me:
```
childadvent@ubuntu:~$ alsamixer
ALSA lib conf.c:1645:(snd_config_load1) _toplevel_:27:0:Unexpected char
ALSA lib conf.c:3425:(snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:3286:(snd_config_hooks_call) function snd_config_hook_load returned error: Argument invalide
ALSA lib conf.c:3671:(snd_config_update_r) hooks failed, removing configuration
cannot open mixer: Argument invalide

```
Any Way To Fix This ?

---

### Post by kerry_s on 2010-06-22
have you tried uninstalling it in synaptic, then reinstalling it.

---

### Post by KingOfDeath on 2010-06-22
> **kerry_s said:**
> have you tried uninstalling it in synaptic, then reinstalling it.Yup But Same Damn Problem :( I Still cannot open alsamixer

---

### Post by KingOfDeath on 2010-06-22
Okay I edited the asound.conf and deleted all what is in it...
Now what happens is

```
childadvent@ubuntu:~$ alsamixer
cannot open mixer: No File or document of that type

```

---


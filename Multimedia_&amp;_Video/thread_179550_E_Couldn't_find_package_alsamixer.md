---
title: "E: Couldn't find package alsamixer"
date: 2006-05-20
forum: Multimedia &amp; Video
---

### Post by tuga on 2006-05-20
Hi,

When I try to install alsamixer with: "sudo apt-get install alsamixer", I get the following:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package alsamixer

How can I install alsamixer?

Thanks

---

### Post by Sef on 2006-05-20
Try this to get download it:

sudo apt-get update

sudo apt-get install gnome-alsamixer alsamixwergui

The second one gives you a graphical interface.

---

### Post by tuga on 2006-05-20
The gnome-alsamixer install was ok. But if i run alsamixer I get the following:

ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.ctl.card'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_getenv returned error: No such file or directory
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib control.c:817:(snd_ctl_open_noupdate) Invalid CTL default

alsamixer: function snd_ctl_open failed for default: No such file or directory

Should I only run the graphical interface "GNOME ASLA mixer" and not "alsamixer"?

---


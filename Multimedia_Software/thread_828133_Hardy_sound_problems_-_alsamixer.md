---
title: "Hardy sound problems - alsamixer"
date: 2008-06-13
forum: Multimedia Software
---

### Post by cairnsww on 2008-06-13
I have no sound at all after upgrading to Hardy.

I have been working through the Comprehensive Sound Problem Solutions Guide at [http://ubuntuforums.org/showthread.php?t=205449&highlight=82801G+Sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=82801G+Sound) and reached the stage where it advised me to check my alsamixer settings by typing alsamixer in a terminal. When I do this, I get:

ALSA lib control.c:874:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so

alsamixer: function snd_ctl_open failed for default: No such file or directory

It seems that this might be THE problem. Any advice on what i do now?

Thanks,
  Bill

---


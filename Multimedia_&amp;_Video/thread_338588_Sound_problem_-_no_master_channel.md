---
title: "Sound problem - no master channel?"
date: 2007-01-14
forum: Multimedia &amp; Video
---

### Post by tjansson on 2007-01-14
I just made a new computer with a Intel Corporation 82801G (ICH7 Family) sound chip on a ASUS P5W DH Deluxe motherboard. 

The sound is great and my 5.1 system works fine but I can't seem to find a master channel in kmix to control the overall sound. The only thing I can do is manually to change the volume of "Front", "Center", "LFE" and the "Side" hcannels  which kind of suck. 

The PCM channel which controlled the overall volume on my old computer doesn't affect the volume at all on this new computer.

---

### Post by sgx on 2007-01-14
> **tjansson said:**
> I just made a new computer with a Intel Corporation 82801G (ICH7 Family) sound chip on a ASUS P5W DH Deluxe motherboard. 

The sound is great and my 5.1 system works fine but I can't seem to find a master channel in kmix to control the overall sound. The only thing I can do is manually to change the volume of "Front", "Center", "LFE" and the "Side" hcannels  which kind of suck. 

The PCM channel which controlled the overall volume on my old computer doesn't affect the volume at all on this new computer.
Try installing alsamixer and alsamixergui, sometimes it will find and
display more possibilities than kmix...start it by the command
alsamixergui
Expand its screen, or use scrollbar to see entire display...hope this helps!

---

### Post by tjansson on 2007-01-15
I actually already tried to start alsamixergui but didn't bother too much since it crashes when I try to open it: 

> 
tjansson@bohr:~$ alsamixergui
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.ctl.card'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_getenv returned error: No such file or directory
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib control.c:816:(snd_ctl_open_noupdate) Invalid CTL default


However it is my experience that kmix and alsamixergui shows the same channel, so I don't think that there is a channel I haven't seen. But thanks for the input! :D

---


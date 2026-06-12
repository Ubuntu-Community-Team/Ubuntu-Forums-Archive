---
title: "Integrated sound Sigmatel not working at all"
date: 2006-06-25
forum: Multimedia &amp; Video
---

### Post by Björn on 2006-06-25
Hi everybode, in my new dell, i have both a x-fi card (which i know has no support yet) and an integrated soundcard. Due to dell, this is a Sigmatel STAC 92xx C-major hd audio.
Because i love music i would like to use the integrated card until creative releases their drivers next spring, but how? 
when i open the volume control, it says: no volume controlled Gstreamer-plugins and/or devices was found (translated from swedish) and when i go to "switcher for multimediasystem"  (also translated) none of ALSA, OSS and ESD is working.
When i try to open alsamixer from the terminal it says

bjorn@bjorn-desktop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

what should i do now?

Thanks in advance for any help, /Björn

---

### Post by Björn on 2006-06-26
I found the solution, :D It was just switched of in the bios, hope it can help someone

---

### Post by Absurd on 2006-06-28
According to Dell, I too have the same integrated audio. However, even when I switch it on from the BIOS Ubuntu **still** cannot detect it.

Anyone know what I should do? (yes, I did remove my PCI sound card--which is a X-Fi too btw)

---

### Post by xdefconx on 2007-09-10
> **Björn said:**
> I found the solution, :D It was just switched of in the bios, hope it can help someone

How to do that step by step in Ubuntu?

*newbiesxhere*

Thanxs

---


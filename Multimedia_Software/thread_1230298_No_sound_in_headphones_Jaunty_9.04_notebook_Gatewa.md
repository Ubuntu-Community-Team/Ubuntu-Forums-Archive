---
title: "No sound in headphones Jaunty 9.04 notebook Gateway M-1617"
date: 2009-08-03
forum: Multimedia Software
---

### Post by nikak406 on 2009-08-03
No sound in headphones Ubuntu 9.04 notebook Gateway M-1617

The system Ubuntu 9.04 is clean and just installed.

I HAVE the sound through built-in speakers, when headphones are plugged out, but i have NO SOUND when the headphones are plugged in.

lspci:

```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
```alsamixer  has everything turned to max, option alsa is selected in sound options.

in etc/modprobe.d/alsa-base.conf I've tried to write to the end in different combinations the next:



```
options snd-hda-intel model=auto, gateway, dell-m42 position_fix=1
```nothing has changed [IMG]http://forum.ubuntu.ru/Smileys/webby/embarrassed.gif[/IMG]

If I missed something, tell me so.

I have a guess, that the model in alsa-base.conf is wrong, but I do not know the right one. Anyway, thank you.

---

### Post by sarfarazkazi on 2009-08-03
Try changing to pulseaudio.

---

### Post by spindzy on 2009-11-05
> **nikak406 said:**
> .......

I have a guess, that the model in alsa-base.conf is wrong, but I do not know the right one. Anyway, thank you.

That much is correct.. in your alsa_base.conf erase all options you've put in there to try to fix the headphones... the ONLY thing you need for a gateway m1617 is ```
options snd-hda-intel model=eapd
```


This will fix it.

---


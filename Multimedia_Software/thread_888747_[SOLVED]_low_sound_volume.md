---
title: "[SOLVED] low sound volume"
date: 2008-08-13
forum: Multimedia Software
---

### Post by weasel7711 on 2008-08-13
I just recently installed Hardy, however the sound volume is extremely low. Without touching the volume on my speakers, which sounds completely normal in XP, I cannot hear a think. It is when I use ubuntu that I need to turn the up extremely high to be able to watch any videos on youtube or listen to music at a decent level, and must remember to turn them down before starting XP or I will blow the walls down with the XP start up sound. I have raised the volume using the keyboard shortcut and manually on the speaker icon in the top right. Any ideas as of why?

---

### Post by null byte on 2008-08-13
> **weasel7711 said:**
> I just recently installed Hardy, however the sound volume is extremely low. Without touching the volume on my speakers, which sounds completely normal in XP, I cannot hear a think. It is when I use ubuntu that I need to turn the up extremely high to be able to watch any videos on youtube or listen to music at a decent level, and must remember to turn them down before starting XP or I will blow the walls down with the XP start up sound. I have raised the volume using the keyboard shortcut and manually on the speaker icon in the top right. Any ideas as of why?
Double click on the speaker icon, raise **PCM** and **Front** to maximum :)

---

### Post by weasel7711 on 2008-08-13
It is at maximum, all of them are.

---

### Post by weasel7711 on 2008-08-13
SOLVED!


I needed to install alsamixer GUI in order to raise the "side" volume bar. Check out post number 7 in the link below.

[http://ubuntuforums.org/showthread.php?t=799091](http://ubuntuforums.org/showthread.php?t=799091)

---

### Post by Garratt on 2008-08-13
1. make sure you have read through the already posted topics and workarounds.

[Comprehensive video multimedia how-to]("http://ubuntuforums.org/showthread.php?t=766683")

[Comprehensive sound stuff how-to]("http://ubuntuforums.org/showthread.php?t=205449")

```
 aplay -l
```

this will list sound card see if its seen.

COPY AND PASTE ALSAMIXER into TERMINAL and check to see if alsa is turned all the way up. 

```
alsamixer
```

alsamixer worked for me after reading those guides. mind you it is only a bit higher, eg i can have speakers set to middle, and alsamixer volumes on high, and desktop sound medium and this produces a reasonable decible. if I turned everything on full i doubt my eardrums would burst, which is what you want idealy.... but for watching movies just a decent sound will do :P

gl.

---


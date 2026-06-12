---
title: "no sound on ubuntu 8.10 ..."
date: 2009-04-11
forum: Multimedia Software
---

### Post by chibourachka on 2009-04-11
hi,
 
 As many i don't get any sound on my laptop,running ubuntu 8.10, despite having my soundcard recognize. I've search through differents forums but without results ...
i did some of the action suggested on the terminal, here is what it yields :

 aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: I82801DBICH4 [Intel 82801DB-ICH4], périphérique 0 : Intel ICH [Intel 82801DB-ICH4]
  Sous-périphériques: 1/1
  Sous-périphéri  aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: I82801DBICH4 [Intel 82801DB-ICH4], périphérique 0 : Intel ICH [Intel 82801DB-ICH4]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: I82801DBICH4 [Intel 82801DB-ICH4], périphérique 4 : Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

when checking in system>preferences>sound, the card appears as " INTEL 82801DB-ICH4 with  AD1981B INTEL 82801DB-ICH4- IEC954 ALSA" ...but running the test gives nothing ...when selecting " auto detect " the test doesn't seem to succeed either , when selecting " INTEL 82801DB-ICH4 with  AD1981B INTEL 82801DB-ICH4- IEC954 OSS " the test still seem endless and blank.
That's where i'm lying for now, helpless so if you know where i should be looking or what to try please help

PS : sound wasn't working on precedent versions either .

---


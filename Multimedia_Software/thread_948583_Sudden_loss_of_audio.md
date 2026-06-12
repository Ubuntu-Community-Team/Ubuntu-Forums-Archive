---
title: "Sudden loss of audio"
date: 2008-10-15
forum: Multimedia Software
---

### Post by vexorian on 2008-10-15
Can anyone help solve this mystery? 
* No updates were involved.
* All that happened was rebooting and then after some time doom wasn't playing any sound, then I noticed nothing had sound. For a second I thought it was physical but when I rebooted to windows, the sound was ok.

```

vx@ubuntuvx:~$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: I82801DBICH4 [Intel 82801DB-ICH4], dispositivo 0: Intel ICH [Intel 82801DB-ICH4]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: I82801DBICH4 [Intel 82801DB-ICH4], dispositivo 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```
I made sure nothing is muted in alsamixer.

---

### Post by vexorian on 2008-10-15
Does anyone have an idea what's going on? Just tested with the 8.04.1 live CD (the same version as the one I installed) and sound works perfectly in the live CD, I also tried just about every howto about getting sound to work in hardy but nothing is helping.

---

### Post by vexorian on 2008-10-16
Ok...

I have no idea what happened, so on those times of desperation I muted everything on alsamixer then I unmuted it on gnome's volume control.

For some reason sound came back.

I officially declare this non-sense. PS: Unlike all the other ubuntu problems I have fixed so far, this one makes me feel dumber.

---

### Post by vexorian on 2008-11-01
Hi, I need help.

Is anyone else using the latest WINE from winehq having this issue?

Whenever I run WINE, the PCM mixer is muted.

---


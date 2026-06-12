---
title: "No audio on HP TX2500 (tablet laptop)"
date: 2009-09-23
forum: Multimedia Software
---

### Post by ilya222 on 2009-09-23
I'v installed 9.04 and the wierd thing that the sound buttons work,
but there is no sound at all.
anyone knows how can i fix it? I googled this issue and found nothing useful..

---

### Post by Favux on 2009-09-23
Hi ilya222,

Welcome to Ubuntu Forums!

The following line works for TX2500 users:
```
options snd-hda-intel index=0 model=toshiba position_fix=1

```
Add it to the bottom of the file "alsa-base.conf" at "/etc/modprobe.d/". Don't worry that it says Toshiba.

To edit it enter in a terminal:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Save, close, and reboot.

Also check to see if the mixer is muted. If so make sure the sliders are up.

I hope this is helpful.

---

### Post by ilya222 on 2009-09-24
hi, thanx, i've done that, and i can see my audio card(s?) in the list
but i still get no sound

**ignore the last one!**
i got i working all fine but the system sounds
instead of nice drums i get a horrible PCspeaker siren.. :|

---

### Post by dado_eyad on 2009-10-04
hi i have the sound working already but when i put a speaker in the speaker jack the sound comes from both the laptop and the speaker
can this be fixed????

---


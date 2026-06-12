---
title: "no sound on HDMI output"
date: 2012-04-05
forum: Multimedia Software
---

### Post by dugommier on 2012-04-05
Hello,
I'm a new user of Ubuntu and can't have sound on my NVidia Hdmi output.
I use Ubuntu 11;10  a fresh version. When I test speakers using system utility i have nothing.

some informations :

> 
aplay -l
**** Liste des Périphériques Matériels PLAYBACK ****
carte 0: NVidia [HDA NVidia], périphérique 3: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 0: NVidia [HDA NVidia], périphérique 7: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 0: NVidia [HDA NVidia], périphérique 8: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 0: NVidia [HDA NVidia], périphérique 9: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0


 I don't have Eld_valid set to 1

> 
grep eld_valid /proc/asound/NVidia/eld*
/proc/asound/NVidia/eld#0.0:eld_valid        0
/proc/asound/NVidia/eld#1.0:eld_valid        0
/proc/asound/NVidia/eld#2.0:eld_valid        0Y
/proc/asound/NVidia/eld#3.0:eld_valid        0


The Alsa full analyse can be find here :

[http://www.alsa-project.org/db/?f=c097231668c98576354f441d9de7e89f36b49032](http://www.alsa-project.org/db/?f=c097231668c98576354f441d9de7e89f36b49032)

Thank you for your helpo

---

### Post by dugommier on 2012-04-05
Sorry, concerning eld_valid, this is the right display :
> 
grep eld_valid /proc/asound/NVidia/eld*
/proc/asound/NVidia/eld#0.0:eld_valid        0
/proc/asound/NVidia/eld#1.0:eld_valid        0
/proc/asound/NVidia/eld#2.0:eld_valid        0
/proc/asound/NVidia/eld#3.0:eld_valid        0



---

### Post by dugommier on 2012-04-05
I solve my problem by changing the driver of the Nvidia card !

---


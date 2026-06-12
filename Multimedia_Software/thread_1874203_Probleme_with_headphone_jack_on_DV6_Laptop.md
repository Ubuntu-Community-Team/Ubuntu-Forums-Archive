---
title: "Probleme with headphone jack on DV6 Laptop"
date: 2011-11-02
forum: Multimedia Software
---

### Post by R3Porter_FX on 2011-11-02
installed 32bit ubuntu 11.10 on my DV6-2190us HP LapTop

the headphone jack and the internal speakers work fine.
But every time connect HeadPhone Jack from front laptop  it come again from both.

in Ubuntu 11.04 Evrything is OK,  and Conector in Sound Setting Output Just Analog speaker is Active.

Run its in Terminal:

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

it gives me :

[http://www.alsa-project.org/db/?f=dc24db0317626b09043aa187a7d439103ff54074](http://www.alsa-project.org/db/?f=dc24db0317626b09043aa187a7d439103ff54074)

Sorry For My Bad English. :"> :(

---

### Post by R3Porter_FX on 2011-11-03
please help me thx

---

### Post by lidex on 2012-01-03
If you're still there, edit this file:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Change this line:
```
options snd-hda-intel model=generic
```
To this:
```
options snd-hda-intel model=hp-dv5 enable_msi=1
```
Save. Close. Reboot.

---


---
title: "headphone with no sound"
date: 2010-06-09
forum: Multimedia Software
---

### Post by narendra_bist on 2010-06-09
hello i use dell studio 1558 and latest ubuntu 10.04 but after installation i could not hear sound from my headphone but internal speakers work properly. plz help me on this.

---

### Post by lidex on 2010-06-09
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by Yellow Pasque on 2010-06-10
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Copy/paste this to the end of the file:
```
options snd-hda-intel model=dell-m6
```
Save. Quit. Reboot.
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/568600](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/568600)

---


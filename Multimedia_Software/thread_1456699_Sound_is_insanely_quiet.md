---
title: "Sound is insanely quiet"
date: 2010-04-17
forum: Multimedia Software
---

### Post by Greenbean209 on 2010-04-17
Thats the problem my sound is insanely quiet. Im running Ubuntu 9.10 right now dual booted with Win 7. Win 7 has perfect sound but it doesnt work right in ubunt. I ran 
```
aplay -l
```
in the terminal and it detected my ATI card. Ive gone into alsa mixer and all the proper channels are on. The only time i can really hear sound is when I plug in my uber sensitive earphone and turn the volume up past 100. Does anybody have any ideas what the problem could be?

---

### Post by hxcobd on 2010-04-17
Have you used the Pulseaudio volume control to check volume levels?

---

### Post by Greenbean209 on 2010-04-17
just checked there all the levels are at 100

---

### Post by lidex on 2010-04-18
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---


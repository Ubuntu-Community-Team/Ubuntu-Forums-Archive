---
title: "speakers wont work"
date: 2010-11-25
forum: Multimedia Software
---

### Post by neonathon on 2010-11-25
Hi there
Ive tried to play music on my gateway solo 2150 laptop on pandora, using a cd, and from my flash drive but nothing comes out of my speakers. Ive tried using the pulse audio mixer as well as alsa. I have also tried using a speaker that plugs into my usb port but with no success. Im running xubuntu 10.10. Anyone have any ideas on how to fix this?

---

### Post by lidex on 2010-11-27
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---


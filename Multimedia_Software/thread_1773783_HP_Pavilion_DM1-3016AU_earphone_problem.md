---
title: "HP Pavilion DM1-3016AU earphone problem"
date: 2011-06-02
forum: Multimedia Software
---

### Post by buknoii on 2011-06-02
hi guys! I bought an hp pavilion dm1z-3016au a few days ago. I installed ubuntu 10.10 hoping that it would detect all the hardware smoothly. any how i encoutered some problems that i was able to fix. the only problem i have is the mic and sounds.. everytime i use the earphones i cant hear anything.

any help would be appricated

laptop model : hp pavilion dm1z-3016au
current os : ubuntu 10.10

---

### Post by lidex on 2011-06-03
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---


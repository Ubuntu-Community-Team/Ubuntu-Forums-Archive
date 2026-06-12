---
title: "Sound from headphones but not from Speakers"
date: 2011-05-09
forum: Multimedia Software
---

### Post by ForrestB on 2011-05-09
Any help would be greatly appreciated.
for the past week I haven't been able to get sound out of my speakers, of my Compaq notebook, only through headphones.   

I've checked all my sound device( maybe not secret ones that I don't know about)
Reinstalled ALSA a few times
Re-installed/upgraded Ubuntu from 10.04 to 11.04

but still no sound from built in speakers, only headphones.     

Any help would be great!!!

---

### Post by lidex on 2011-05-11
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---


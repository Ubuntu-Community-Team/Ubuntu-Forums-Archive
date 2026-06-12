---
title: "video an audio problems"
date: 2010-11-05
forum: Multimedia Software
---

### Post by gordie69 on 2010-11-05
Hi guys trying to recover my video settings tried rovery mode from start up but when I get into ubuntu the screen fuzzy let you can't see your curser to select anything and everything worked great but also no sound its a gateway laptop with intel celeron 1.5 and 1 gig ram intergrated sound an video, video is a 64 meg. Can someone head me in the right direction for some help.
I love ubuntu 10 better then any windows period.

---

### Post by lidex on 2010-11-06
Did you fix the graphics issue?
For audio I'll need more info. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---


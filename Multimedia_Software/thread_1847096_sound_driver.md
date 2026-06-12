---
title: "sound driver"
date: 2011-09-20
forum: Multimedia Software
---

### Post by ashishs9210a on 2011-09-20
how can i solve the problem of sound? there is no sound when i play a video in the vlc and another media player.how can sound driver find in ubuntu 10.04?please tell me

---

### Post by nothingspecial on 2011-09-20
Moved to Multimedia & Video

---

### Post by nothingspecial on 2011-09-20
Hi,

you need to give some details of your sound card

Open a terminal and type ```
aplay -l
```

Post the results in a new post back here.

---

### Post by lidex on 2011-09-21
Do you have login/gdm sound? Can you play mp3 files?

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---


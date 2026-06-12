---
title: "Sound"
date: 2011-05-08
forum: Multimedia Software
---

### Post by DrZee88 on 2011-05-08
Got another problem, sometimes my sound just disappear. 

Any ideas what is the problem here?

---

### Post by DrZee88 on 2011-05-08
Can't find explanation, few days ago there was sound everywhere except VLC player, now i dont have sound anywhere.

---

### Post by DrZee88 on 2011-05-08
Now I'm getting error: "Waiting for sound system to respond"

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


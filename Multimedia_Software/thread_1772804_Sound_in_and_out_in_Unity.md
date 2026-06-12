---
title: "Sound in and out in Unity"
date: 2011-06-01
forum: Multimedia Software
---

### Post by Lars Noodén on 2011-06-01
Where in Unity can I specify input and output sound devices?
Right now I have a USB headset  with microphone and no sound is going to it.  No sound is going to the built-in internal speaker, either.

---

### Post by lidex on 2011-06-04
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---


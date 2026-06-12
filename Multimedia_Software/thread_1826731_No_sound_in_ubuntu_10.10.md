---
title: "No sound in ubuntu 10.10"
date: 2011-08-17
forum: Multimedia Software
---

### Post by peeyushK on 2011-08-17
I installed ubuntu 10.10 some days back. but the sound is not coming. neither song nor video. Even sound at startup is also not coming. Please help me.

---

### Post by lidex on 2011-08-17
> **peeyushK said:**
> I installed ubuntu 10.10 some days back. but the sound is not coming. neither song nor video. Even sound at startup is also not coming. Please help me.

The "P" word always gets me.
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---


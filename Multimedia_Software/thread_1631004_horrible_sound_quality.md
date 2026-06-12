---
title: "horrible sound quality"
date: 2010-11-26
forum: Multimedia Software
---

### Post by Nortesidin on 2010-11-26
having some massive sound quality issues... my sound sounds so incredibly horrible.. it sounds like my speakers are blown out, all crackly and shitty. at a loss because i do have sound, it just sounds horrible. Any pointers as where i can start to investigate?

---

### Post by Nortesidin on 2010-11-26
Update, just was listening to a song on facebook, and sound just cut out completely... anyone got any ideas?

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


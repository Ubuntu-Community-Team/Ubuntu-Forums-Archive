---
title: "Sound not working"
date: 2011-01-16
forum: Multimedia Software
---

### Post by camn on 2011-01-16
Hi... the sound on this laptop isn't working... It has an "Intel Corporation 82801I (ICH9 Family) HD Audio Controller" sound card... What's wrong? :o

---

### Post by lidex on 2011-01-16
Hard to say, you provided so very little info. If you click on volume-indicator and select 'sound preferences' make sure your output is not muted and you have the correct preference selected.
Otherwise do this. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---


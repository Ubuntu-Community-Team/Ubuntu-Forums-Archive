---
title: "Sound stopped working"
date: 2010-10-06
forum: Multimedia Software
---

### Post by Jolicoeur on 2010-10-06
Sound worked in 9.10, could not install 10.04, sound worked in 10.10 then stopped after three days, reloaded 9.10 and sound does not work.  Is this at all common?  Does this sound like Ubuntu having a problem or does it sound like my hardware?  Please help if you can.  :confused:

---

### Post by lidex on 2010-10-07
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---


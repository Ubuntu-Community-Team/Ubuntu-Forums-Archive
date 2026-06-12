---
title: "NO sound in ubuntu ultimate edition 2.8"
date: 2011-06-15
forum: Multimedia Software
---

### Post by sanoopmv on 2011-06-15
Hi,

Am using Ubuntu Ultimate Edition 2.8 which is build on Ubuntu 10.10 Maverick.

Am using it in my laptop

Toshiba Satellite c660 -p 5012

Am having no sound at all the sound hardware tab shows no sound cards


But in the system hardware tab it says Intel 5 series/3400 series HD audio



HELP ME PLS!!!!!!!!!!!!!!!!!!!!!!!!!:(

---

### Post by sanoopmv on 2011-06-15
[QUOTE=sanoopmv;10941143]Hi,

Am using Ubuntu Ultimate Edition 2.8 which is build on Ubuntu 10.10 Maverick.

Am using it in my laptop

Toshiba Satellite c660 -p 5012

Am having no sound at all the sound hardware tab shows no sound cards


But in the system hardware tab it says Intel 5 series/3400 series HD audio

aplay -l doesn't display any device

but the audio device remain UNCLAIMED


HELP ME PLS!!!!!!!!!!!!!!!!!!!!!!!!!:(

---

### Post by lidex on 2011-06-18
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---


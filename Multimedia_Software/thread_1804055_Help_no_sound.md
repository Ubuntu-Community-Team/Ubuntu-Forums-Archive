---
title: "Help: no sound"
date: 2011-07-14
forum: Multimedia Software
---

### Post by gnznt on 2011-07-14
Fresh install of Ubuntu 10.04 LTS Lucid.  No sound.  Tried to use Rhythmbox and downloaded plug-ins for mp3 support; no sound.  Please help.  :(

---

### Post by lidex on 2011-07-14
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---


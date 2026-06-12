---
title: "Having sound trouble."
date: 2010-08-27
forum: Multimedia Software
---

### Post by Nukester on 2010-08-27
My volume is ok on Ubuntu 10.4, but if I turn up the volume to some extent, it turns grainy and staticky(sp?). The base especially, I can't jam any songs with a lot of bass. I'm wondering if I'm supposed to download any codecs or software, my sound card is integrated into my laptop's motherboard. Works fine on Windows 7 and XP, so no problems with hardware.

---

### Post by lidex on 2010-08-28
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---


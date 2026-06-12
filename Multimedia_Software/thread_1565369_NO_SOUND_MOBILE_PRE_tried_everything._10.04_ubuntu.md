---
title: "NO SOUND MOBILE PRE tried everything. 10.04 ubuntu"
date: 2010-08-31
forum: Multimedia Software
---

### Post by StudioB on 2010-08-31
**alsamixer > no such file or directory** 
i read through and spent an hour trying to fix my maudio mobile pre
i tried uninstalling and reinstalling alsa. 
i tried getting a new updated also from their site and installing it. 
and no luck.
i put the error message i got from trying to run **[COLOR=#ff0000]alsamixer[/COLOR]** in the title.
i dont know why it says that there are no alsa drivers when ive tried to install them 2 different ways!
(i am new to ubuntu)

---

### Post by StudioB on 2010-09-01
wow...no responses. im just gonna reinstall the whole OS.

---

### Post by lidex on 2010-09-03
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---


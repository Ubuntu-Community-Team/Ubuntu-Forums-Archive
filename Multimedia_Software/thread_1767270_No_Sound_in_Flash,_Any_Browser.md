---
title: "No Sound in Flash, Any Browser"
date: 2011-05-25
forum: Multimedia Software
---

### Post by yoramsk on 2011-05-25
Sound from other applications is fine. I have tried removing and reinstalling the flash packages but it did not help. Any ideas on how to trouble shoot this further? I am running 11.04 64bit.  It was working fine earlier but something seems to have screwed it up.

---

### Post by lidex on 2011-05-25
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications-> Accessories-> Terminal"]

---

### Post by yoramsk on 2011-05-25
Here is the link.

[http://www.alsa-project.org/db/?f=ff4c87b0b5402389532da9edb6636d2b14204741](http://www.alsa-project.org/db/?f=ff4c87b0b5402389532da9edb6636d2b14204741)

Thanks so much for the help.

---

### Post by irish66 on 2011-05-26
Hi, i believe I have the same problem. I can hear sound if i play something located on my drives, but not if played on a browser.
here is the link
[http://www.alsa-project.org/db/?f=7f9ca373f616a79abcc60adf1148649f41b4240c](http://www.alsa-project.org/db/?f=7f9ca373f616a79abcc60adf1148649f41b4240c)

Note. I thought I posted on this problem before. I have been using windows for the past 3 weeks. My linux application is linux mint.

---

### Post by yoramsk on 2011-05-27
Bump. Bump.  Please help.

---

### Post by lovinglinux on 2011-05-27
> **yoramsk said:**
> Bump. Bump.  Please help.

Try the solution provided at [http://www.webgapps.org/tutorials/firefox/troubleshooting/flash-issues-and-solutions](http://www.webgapps.org/tutorials/firefox/troubleshooting/flash-issues-and-solutions)

---

### Post by lidex on 2011-05-27
If above reply is not helping, have a look here:
[http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---


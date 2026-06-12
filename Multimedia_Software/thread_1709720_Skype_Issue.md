---
title: "Skype Issue"
date: 2011-03-18
forum: Multimedia Software
---

### Post by goguy on 2011-03-18
Howdy,

I am attempting to use Skype on 10.10. I have the video running, I unmuted the mic, I have no option to change to anything from pulse audio server for any of the sound devices. When I was talking to someone, they said the sound they were getting from me was like "electronic noise".Using Gnome and System is an HP Pavillion DV7 1448dx.

---

### Post by lidex on 2011-03-18
Vitals please. 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

Using internal mic?

---

### Post by goguy on 2011-03-19
Vitals, and yes, I am attempting to use the internal mic.

[http://www.alsa-project.org/db/?f=ba1bea4ca48ca0fae0ba50f888970dbff2000be1]("http://www.alsa-project.org/db/?f=ba1bea4ca48ca0fae0ba50f888970dbff2000be1")

---

### Post by lidex on 2011-03-19
How does it sound with 'sound recorder'?
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=hp-dv5 enable_msi=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by goguy on 2011-03-21
That command fixed it, but today, I could not see the other person on the end but they could see me, don't know if that was a skype issue or something with ubuntu, but they could hear me today and sound recorder also worked.

---


---
title: "Sound only through laptop speakers, none through headphones"
date: 2010-12-24
forum: Multimedia Software
---

### Post by Paanini on 2010-12-24
Hi I just bought a new laptop, a Lenovo Z460.
I'm running Ubuntu 10.10 on it in addition to the Windows 7 Home Basic it came pre-installed with.
The problem is, whenever any kind of audio is to be played, it plays it only through the laptop speakers, even when my headphones are plugged into the jack.
This problem does not exist in windows, so I'm assuming it has to do with some drivers or alsa settings.
Any help ?

---

### Post by Ploozi on 2010-12-25
It's a bug within ALSA, I semi-fixed mine on my Toshiba Satellite by removing all ALSA-related applications and installed OSS4, and viola, it worked. But me being a little slow, I fiddled a little bit more into it, and then ruined it.

---

### Post by lidex on 2010-12-25
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Syed75 on 2010-12-25
Just change the output. 

<System<Preferences<Sound<Output

Change it to apply to what your using.

---

### Post by Paanini on 2010-12-28
I fixed it !
I found a similar case on another thread, which pointed me to this page :

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

I followed the instructions there, installed 'linux-alsa-driver-modules' and it works perfectly now.

Thank you :)

---


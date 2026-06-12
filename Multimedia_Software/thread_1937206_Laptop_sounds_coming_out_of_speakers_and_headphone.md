---
title: "Laptop sounds coming out of speakers and headphones?"
date: 2012-03-07
forum: Multimedia Software
---

### Post by Tyharo on 2012-03-07
I have an AsusG72GX laptop and I've recently install Ubuntu on a second HDD I installed. Ive used Ubuntu on plenty of machines but Ive never had a sound issue like this. Even though my headphones are plugged in sound continues to come out of my laptop speakers along with my headphones. Ive tried using alsamixer but I didnt have any luck. Is there any fix for this yet, or do I have to wait on updates to fix this later?

---

### Post by Yellow Pasque on 2012-03-07
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Tyharo on 2012-03-08
heres the link that it produced:
[http://www.alsa-project.org/db/?f=b2c2d82b3ee3f35c080d8cfe5d5d729679cc9f4a](http://www.alsa-project.org/db/?f=b2c2d82b3ee3f35c080d8cfe5d5d729679cc9f4a)

---

### Post by Tyharo on 2012-03-09
Any luck figuring out the problem?:confused:

---

### Post by Yellow Pasque on 2012-03-09
Try adding the following line to /etc/modprobe.d/alsa-base.conf :
```
options snd-hda-intel model=asus-mode8
```

---

### Post by Tyharo on 2012-03-09
No luck, or do I need to do anything in Alsa-mixer?

---

### Post by Yellow Pasque on 2012-03-09
Did you reboot (or at least reload alsa)?

---

### Post by Tyharo on 2012-03-10
Yes, I put the code in and restarted. Do I need to change any settings in alsamixer Or Is this issue only being cause by the config file?

---

### Post by Yellow Pasque on 2012-03-12
The only other thing I can suggest is using the latest alsa kernel module:

```
sudo apt-add-repository ppa:ubuntu-audio-dev/alsa-daily
sudo apt-get update
sudo apt-get install alsa-hda-dkms
```

---


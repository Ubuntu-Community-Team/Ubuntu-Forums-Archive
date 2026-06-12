---
title: "headphone jack does not cut off speakers in 12.04"
date: 2012-08-05
forum: Multimedia Software
---

### Post by Bacilio on 2012-08-05
i've been on 11.04 from when it was released up till August 4th. everything was working fine till i plugged my headphones in. i could hear sound from my headphones but from my laptop speakers aswell. help would be greatly appreciated since im a bit new to modifying or adjusting settings to Ubuntu, since its always worked perfect for me. can anyone help me please?

---

### Post by ajgreeny on 2012-08-05
Normally this is all done with a microswitch in the headphone socket, so try plugging in and out vigorously a few times and wiggling the plug around a bit in the socket.

---

### Post by Bacilio on 2012-08-05
i did for some time yesterday.. and still no change.

---

### Post by Yellow Pasque on 2012-08-06
More info please: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Bacilio on 2012-08-06
[http://www.alsa-project.org/db/?f=123f838a2ef009934b886297446643f6ce208dfc]("http://www.alsa-project.org/db/?f=123f838a2ef009934b886297446643f6ce208dfc")

---

### Post by Yellow Pasque on 2012-08-07
Open your /etc/modprobe.d/alsa-base.conf file for editing:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

Remove all of the lines that contain "options snd-hda-intel model="

Add this line:
```
options snd-hda-intel model=acer
```
Save. Quit. Reboot.

---

### Post by Bacilio on 2012-08-07
i did, rebooted and all that changed was no sound coming from the headphone jack anymore.. i plug in headphones and speakers still dont get cut off and no sound from headphones anymore.. i tried different headphones too.. i get a feeling i might have to wait for a later release of 12.10... but i would greatly appreciate it if i could get it fixed sooner than that.

---


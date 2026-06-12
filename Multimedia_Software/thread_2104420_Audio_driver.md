---
title: "Audio driver"
date: 2013-01-13
forum: Multimedia Software
---

### Post by QuiE on 2013-01-13
I have an alienware m14x just installed ubuntu completly and i have the problem that the speaker work perfectly but when i connect some earphones to the computers output it dosent recognize them and still uses the speakers ...

---

### Post by miegiel on 2013-01-13
Wich ubuntu are you using? In 12.04 there is this bug: [https://bugs.launchpad.net/ubuntu/precise/+source/pulseaudio/+bug/946232?comments=all](https://bugs.launchpad.net/ubuntu/precise/+source/pulseaudio/+bug/946232?comments=all)

btw, welcome to ubuntu forums

---

### Post by QuiE on 2013-01-13
Thanks, im using the ubuntu 12.10

---

### Post by Yellow Pasque on 2013-01-13
Open /etc/modprobe.d/alsa-base.conf for editing
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Add this line (copy/paste) to the end of the file:
```
options snd-hda-intel model=alienware
```
Save the file, quit gedit, and resart ALSA with:
```
sudo alsa reload
```

If it's still not working correctly, remove the line you added, restart ALSA, and file a bug using apport.

---


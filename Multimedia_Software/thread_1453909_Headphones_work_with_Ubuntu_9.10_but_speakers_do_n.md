---
title: "Headphones work with Ubuntu 9.10 but speakers do not"
date: 2010-04-13
forum: Multimedia Software
---

### Post by stork1230 on 2010-04-13
I have a HP Pavilion notebook dv4. I can plug in the headphones and they work fine. But external speakers do not work. Any advice?

---

### Post by lidex on 2010-04-13
Go to this page and install alsa-backports.
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
Run this command in a terminal="Applications>Accessories>Terminal":
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Add these lines at the bottom of that file:
```
options snd-hda-intel enable_msi=1
options snd-hda-intel model=hp-dv5

```
Save. Close. Reboot.

---

### Post by stork1230 on 2010-04-13
Wow thanks!

---


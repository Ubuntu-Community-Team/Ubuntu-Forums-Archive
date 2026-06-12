---
title: "Headphones sound weird"
date: 2013-11-08
forum: Multimedia Software
---

### Post by Shadius on 2013-11-08
Hey everybody!

My problem is that I'm not hearing any kind of bass through my headphones. On other systems (I have a Mac & Windows also), the bass kicks, but on Ubuntu it's not as bassy. It just doesn't have the same sound as on other devices. I'm wondering if I need to configure something here. Please help, I love to listen to music!

---

### Post by Shadius on 2013-12-22
Bump

---

### Post by Yellow Pasque on 2013-12-23
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Shadius on 2014-01-04
> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Here is the [link]("http://www.alsa-project.org/db/?f=c096b079583790e3cc8342813763bc5222a8b239")

---

### Post by Yellow Pasque on 2014-01-04
I'd suggest trying the latest driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
Also, try a player with an equalizer built in like gmusicbrowser.

---

### Post by Shadius on 2014-01-11
I'll try it. Thanks.

---

### Post by Shadius on 2014-01-25
How do I check what current sound driver is installed?

---

### Post by Yellow Pasque on 2014-01-25
You run the alsa info script as before and close to the top of all the info it spits out, you see:

> !!ALSA Version
!!------------
[B]
Driver version:     1.0.24[/B]
Library version:    1.0.25
Utilities version:  1.0.25

Note that with modern versions of ALSA, they just use the same version number as the kernel.

---


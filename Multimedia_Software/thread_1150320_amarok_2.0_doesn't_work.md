---
title: "amarok 2.0 doesn't work"
date: 2009-05-06
forum: Multimedia Software
---

### Post by chuse on 2009-05-06
Hi to all.
I recently upgrade my system from Ubuntu 8.04 to 8.10 and then to 9.04. In this last version, I also upgraded Amarok, but it doesn't work:
The program load with a message that says

"**Phonon KDE's multimedia library**
The audio playback device **HDA NVidia (ALC662 Analog)** does not work.
Falling back to **PulseAudio**"

So, I play a song but it doesn't reproduce the sound. I already reinstalled phonon-related packages, but I think that's not the problem.

Please help me, thanks
chuse

---

### Post by Aereal on 2009-05-06
Exactly the same problem here. Been working for a few hours to work it out. If I found something I'll post it here.

---

### Post by garethfnb on 2009-05-06
had the same problem now.  working now
sudo apt-get install libxine1-ffmpeg

---

### Post by ultrabatman on 2009-06-28
I had the same problem for weeks before I finally got it to work:
```
sudo apt-get install libxine1 libxine1-ffmpeg phonon-backend-xine
mv ~/.kde/share/config/phonondevicesrc ~/.kde/share/config/phonondevicesrc.save
```
I then logged out and back in again, and Amarok was working.  I noticed that the phonondevicesrc file was *not* recreated, so I don't know whether this will break other things, but whatever, it made Amarok work.
I should mention that my sound device is:
HDA Intel - VT1708B, and lspci sez it's "ICH7 family".

---

### Post by tempus on 2009-06-29
> **Aereal said:**
> Exactly the same problem here. Been working for a few hours to work it out. If I found something I'll post it here.

same here! Amarok does not wok on 2 computers yet exaile does.

---


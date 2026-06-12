---
title: "Sound misconfigured."
date: 2010-09-09
forum: Multimedia Software
---

### Post by honestguvnor on 2010-09-09
After upgrading to 10.04 I lost the sound like a substantial number of other people. Browsing the posts has allowed me to temporarily restore it by performing the following actions:
1. installing the gnome-alsa mixer program and the pulseaudio volume control program.
2. running the alsa mixer program and unmuting various channels to get sound through the speakers/headphones.
3. running the pulse-audio program and waggling the microphone volume settings to get sound through the microphone.

I have to repeat 2. and 3. after every reboot.

I would like to implement a permanent fix and to understand more about how/why the sound is misconfigured. Thanks for any suggestions.

---

### Post by ericrcan on 2010-09-09
I was having the same problem as well for my netbook. I tried many things and I still couldnt get it to work. I finally tried this and now it works. Try this out:

Open up terminal:

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

Add this at the very bottom```
options snd-hda-intel index=0 model=auto
```

Reboot, then after reboot open the terminal gain and run

```
alsamixer
```

Make sure all the volumes are turned up using the arrow keys. IF there an M at the bottom of any of them, press M to unmute it and teh M will disapear. Try that out :D

---

### Post by honestguvnor on 2010-09-09
Thanks for the input. I played with the options in the configuration file and it did indeed successfully address the ALSA issues. 

Unfortunately, the pulseaudio issue with the microphone still remains. It seems to get fixed by fiddling with pretty much anything related to pulseaudio configuration.

---


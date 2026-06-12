---
title: "PulseAudio recently blocked from starting"
date: 2010-07-30
forum: Multimedia Software
---

### Post by daltore on 2010-07-30
Sometime last week, my volume control disappeared.  Upon investigating, I realized that the PulseAudio daemon was not running.  When I tried to start it (both by command line and by graphical interface), it errored and refused to start.  It is my impression that some other program is using the sound card, but I have been unable to find anything.  I've removed all of my local media program configuration files, but nothing seemed to change.

1)  Any suggestions for finding the program that is locking the sound card?
2)  Any suggestions at all for fixing this problem?

---

### Post by lidex on 2010-07-30
Remove old config files:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Reboot**
Now this output please:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---


---
title: "Need to stop Pulseaudio from loading"
date: 2008-07-29
forum: Multimedia Software
---

### Post by Wee Aldo on 2008-07-29
Hello all...

Have found a problem with the pulseaudio service, it keeps transmitting packets across my LAN and is preventing my other Ubuntu box from going online. It seems to be only this one machine that has the problem, re-niceing the priorities does not help, I have to manually kill the process each time I log on to this particular machine (the one with the problem). System monitor reports that the pulseaudio settings are identical on both machines.

Thanks in advance :->

---

### Post by TenPlus1 on 2008-07-29
Going into Sessions and unticking PulseAudio might help, either that or do what I did and uninstall PulseAudio altogether...  Sound still works great using ALSA...

---

### Post by Wee Aldo on 2008-07-29
Thanks for the quick reply...tried the sessions option with no results...pulseaudio still keeps firing packets across the LAN...if I elect to uninstall it from synaptic, it wants to remove Ubuntu desktop as well, any thoughts?

---

### Post by TenPlus1 on 2008-07-31
You can safely remove ubuntu-desktop without any problems, it's just a meta-package, but when Ibex is out, you may either have to re-install it to upgrade properly or do a full re-install...  just a warning!

---

### Post by markbuntu on 2008-07-31
You need to use PulseAudio Device Chooser to turn off the network services.

---


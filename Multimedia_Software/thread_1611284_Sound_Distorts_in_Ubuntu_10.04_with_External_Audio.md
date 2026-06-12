---
title: "Sound Distorts in Ubuntu 10.04 with External Audio Interface"
date: 2010-11-01
forum: Multimedia Software
---

### Post by BcRich on 2010-11-01
Hi 
Just thought I'd mention this as it might help somebody out there :)
I have an external audio interface that is supported by alsa and works really well with ubuntu 10.04. The only problem is that on my studio monitors I can clearly hear that the sound from ubuntu is distorted, like there is too much gain somwhere. Since my audio interface (Lexicon Omega) has an output level knob on the interface, ALSA does not have a level slider (software) through any mixer (eg GNOME ALSA mixer).
In order to stop the distorting sound problem, ie the signal input to my external audio interface is too "hot"
first install PulseAudio Volume Control (referred to as pavucontrol in repos)
in PulseAudio Volume Control configuration tab, set "profile" of your external sound interface to "off"
log out, and when you log in again your problem should be solved. 
hope that helps, it worked for me :)

---

### Post by snapback77 on 2010-11-14
Thanks.  I got the new Music Sreamer II because it had asynchronous jitter control and 96/24 capability.  I have enjoyed the free samples I discovered through Computeraudiophile.com, but am reluctant to start getting high resolution downloads because of a very loud noise that strikes (like a very loud pop) randomly while listening. I hope find a solution.  There are not very many audiophiles like us on the forum.  I appreciate your contribution.

---

### Post by BcRich on 2010-11-15
hi snapback77
i hope my suggestion can solve your audio problem. don't know if it's going to help you but i found this very long (and comprehensive) guide to configuring audio settings in ubuntu 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
it's a bit old, but a lot of the tricks are still very useful and it certainly helped me :)
good luck

---


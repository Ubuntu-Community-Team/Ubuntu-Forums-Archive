---
title: "no sound cards found"
date: 2011-01-30
forum: Multimedia Software
---

### Post by badnaam on 2011-01-30
tried to install linuxant drivers which failed and then I uninstalled it. Now sound does not work, installed alsa backports again, installed alsa, alsautils again as well. no luck.

aplay -l 


aplay: device_list:235: no soundcards found...


This is on maverick.

What do I do now? Please help!

---

### Post by badnaam on 2011-01-31
This is what I get when I reload alsa.


username@usernamelecorpio:~$ sudo alsa reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/username/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

---

### Post by badnaam on 2011-02-01
Please help!

---

### Post by lidex on 2011-02-01
Did you confirm your codec as conexant before installing linuxant driver? Obviously your alsa install is borked, try this to reset.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

---


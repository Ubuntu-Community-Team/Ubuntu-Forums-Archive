---
title: "Alsa Not Work: No Sound/ Dummy Output Only"
date: 2013-05-14
forum: Multimedia Software
---

### Post by bbh4real on 2013-05-14
Hello,
Recently I was trying to use Ardour and I had problems with JACK. After unsuccessfully trying to resolve the issue, I restarted, and found that my sound was no longer working. cat /proc/asound/cards reveals --no soundcards--. I have already attempted to uninstall/reinstall pulseaudio and alsa. It so happens that when I am force-reloading or reloading alsa, it hangs after loading the final driver (snd-timer). I used the script mentioned in other posts and this is a link to my output: [http://www.alsa-project.org/db/?f=8cac88f5d849ab5b97f67747f64a8b5919bc234f](http://www.alsa-project.org/db/?f=8cac88f5d849ab5b97f67747f64a8b5919bc234f) .
Please, any help is appreciated, and I would really prefer not to a complete reinstall. Thank you.

---

### Post by Yellow Pasque on 2013-05-14
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984)

---

### Post by bbh4real on 2013-05-14
So I need to use the workaround or wait for a patch?

EDIT:
Okay the workaround seems to have solved the issue. Anyone interested can find it here: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

Thank you for the help, very much appreciated :)

---


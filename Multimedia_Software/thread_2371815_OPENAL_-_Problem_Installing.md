---
title: "OPENAL - Problem Installing"
date: 2017-09-19
forum: Multimedia Software
---

### Post by al14 on 2017-09-19
I'm looking to get a new or working version of 'OPENAL' to get the sound working for a screensaver I installed.

 Without 'OPENAL', no sound-

It's for Ubuntu Unity 16.04 Xenial-

Thanks!

---

### Post by al14 on 2017-09-19
Okay, I found ['OpenAL Soft']("https://sourceforge.net/projects/openal-soft/") at sourceforge, but I cant install it.

It's a tar.bz2 file-

I'm not totally linux illiterate, I install through ubuntu software center, synaptic, ppa's through terminal and of course, the easy .deb's....but I haven't reached the learning-curve required for the tar.bz2's yet....

Can anyone please explain how I can get this sourceforge file installed?

Thanks in advance!

---

### Post by Yellow Pasque on 2017-09-19
We already have openal soft available in the repo (libopenal1). There is no need to install from a tarball. To confirm you have it available on your system:
```
sudo apt-get install openal-info
openal-info
```

---

### Post by al14 on 2017-09-19
> **Temüjin said:**
> We already have openal soft available in the repo (libopenal1). There is no need to install from a tarball. To confirm you have it available on your system:
```
sudo apt-get install openal-info
openal-info
```

Thanks...I got openal installed-

After tweaking the screensaver, the sound worked for awhile, then quit-

It has a linux version, but apparently is dedicated to Windoze....

It was too noisy anyway :biggrin:

---


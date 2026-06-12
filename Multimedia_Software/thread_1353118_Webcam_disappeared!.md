---
title: "Webcam disappeared!"
date: 2009-12-12
forum: Multimedia Software
---

### Post by iceman85 on 2009-12-12
Ok guys, i'm back to write to you because i need help.

Probably with the last updates, my webcam is disappeared from the system. And i don't know where or how to fix this problem!I've thought that was a problem derived from Skype...but when i've tried aMSN has been the same.

Problem in the problem....

i'm not able to install Skype from the Medibuntu package!!! :(

---

### Post by RedSingularity on 2009-12-12
What happens when you try to install skype from medibuntu?

---

### Post by iceman85 on 2009-12-12
> **RedSingularity said:**
> What happens when you try to install skype from medibuntu?

i follow that code to get the repository:
```
sudo wget \
  --output-document=/etc/apt/sources.list.d/medibuntu.list \
  http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list &&
sudo apt-get --quiet update &&
sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get --quiet update
```but then, when i go to synaptic to search Skype package, i don't find it in the list!!
during the afternoon i've seen that, if go to the Medibuntu's official site: [http://packages.medibuntu.org/karmic/index.html](http://packages.medibuntu.org/karmic/index.html) it is possible to download the .deb of skype (v. 2.1.0.47-0medibuntu2). Installing that version, i see my webcam with green flashes in the preview from the Options. 

This was the last version (skype v. 2.0.0.72-0medibuntu4) that surely works without the green flashes!

by the way, the problem of the cam is solved after a general restart of the computer.

---

### Post by iceman85 on 2009-12-12
[http://ubuntuforums.org/showthread.php?t=1306368&page=2](http://ubuntuforums.org/showthread.php?t=1306368&page=2)


here there is the answer!

---


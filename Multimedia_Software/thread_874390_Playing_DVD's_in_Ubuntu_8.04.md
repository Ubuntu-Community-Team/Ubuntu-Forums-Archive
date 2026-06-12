---
title: "Playing DVD's in Ubuntu 8.04"
date: 2008-07-29
forum: Multimedia Software
---

### Post by lmfrolich on 2008-07-29
What is the best way to view DVD's?  I've got Movie Player, KM PLayer and xgine and none of them seem to work with Ubuntu 8.04   Any suggestions?
I also followed the advice on a command line for the terminal window and that didn't help.

LF

---

### Post by scragar on 2008-07-29
install **ubuntu-restricted-extras** like so
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by mordak13 on 2008-07-29
Open Synaptic and search for "Ubuntu Restricted Extras" and check that for installation. It install the libdvdread3 & ffmpeg packages as well as several others. I think this should do it. It's been a while since I've needed DVD playback as I have a new 46" LCD TV and a PS3 for Blueray movies. Good luck.

---

### Post by fenian on 2008-07-29
Open a terminal and enter...

> sudo apt-get install ubuntu-restricted-extras

then to add the medibuntu repository,enter...

> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

then enter the gpg key...

> sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

then to add libdvdcsss (needed to decode DVD) enter...

> sudo apt-get install libdvdcss2

---

### Post by mordak13 on 2008-07-29
> **fenian said:**
> Open a terminal and enter...



then to add the medibuntu repository,enter...



then enter the gpg key...



then to add libdvdcsss (needed to decode DVD) enter...

Ahhh yes I forgot about the libdvdcss2 library I remember that controversy like it was yesterday. :popcorn:

---


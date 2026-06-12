---
title: "Codecs for music and video"
date: 2010-01-06
forum: Multimedia Software
---

### Post by ubuncha on 2010-01-06
I have just installed Ubuntu 9.04 and was wondering where I can download codecs for playing video and also sound files (music).
I can record in sound recorder (I see the level going up and down when I clap my hands) but there is no playback.

---

### Post by jimmers on 2010-01-06
Try this 

sudo apt-get install w32codecs libdvdcss2

sudo apt-get install ubuntu restricted extras

---

### Post by FakeOutdoorsman on 2010-01-06
> **jimmers said:**
> Try this 

sudo apt-get install w32codecs libdvdcss2
These packages require enabling of the [Medibuntu](http://medibuntu.org/) repository.
> **jimmers said:**
> sudo apt-get install ubuntu restricted extras
This package is spelled *ubuntu-restricted-extras*.

---

### Post by HappyFeet on 2010-01-06
The easy way to get most codecs is:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then
```
sudo apt-get install non-free-codecs libdvdcss2
```

---

### Post by ubuncha on 2010-01-09
Thanks for the help guys!

Although I'm having trouble getting online (I'm using another computer for this post) because the only option I have to connect to the net is through 56k dial-up modem. I'm currently trying to work out how to get Ubuntu to recognize my modem.

Is there anyway to download the codecs and save them to USB memory stick, and then install them to ubuntu this way?

Thanks again.

---


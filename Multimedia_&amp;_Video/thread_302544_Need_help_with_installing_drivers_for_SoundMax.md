---
title: "Need help with installing drivers for SoundMax"
date: 2006-11-18
forum: Multimedia &amp; Video
---

### Post by guliver on 2006-11-18
The problem with original drivers is that if I put mixer on more than a half of maximum I got distortion. 
Also it does not record voice from the microphone properly.

I downloaded ASUS drivers for Linux and first set of commans are to build AC97 ALSA driver:

> 6. The three basic commands needed to build the AC97 ALSA driver 
are summarize here:  (These commands should be executed from the 
root account.)

	./configure --with-cards=intel8x0
	make install
	./snddevices

When I run **./configure --with-cards=intel8x0** I got following output:

```
user@UBUNTU:~/Desktop/audio/Linux/alsa-driver-0.9.1adi$ ./configure --with-cards=intel8x0
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable cc found in $PATH

```

Can anybody help me to install this? :-k

---

### Post by paddy2706 on 2006-12-21
you need to install gcc. just execute apt-get build-dep alsa, this should install all neccessary packages

---


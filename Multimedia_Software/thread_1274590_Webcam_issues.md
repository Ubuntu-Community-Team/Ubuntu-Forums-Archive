---
title: "Webcam issues"
date: 2009-09-24
forum: Multimedia Software
---

### Post by Saucisse on 2009-09-24
Hi guys,
I am pretty new in the Linux world and I have some difficulties doing basic stuff. Okay yesterday I got to install Skype thanks to the forum, and today I am stuck with the webcam and sound installation.
When I plug in my webcam, there is the green light on the webcam on as if I was constantly using it. But when I am making a call on Skype, there is no webcam and no microphone. It doesnt recognize it actually. Maybe bcause its a Microsoft ? :smile:
Its a LifeCam VX-1000.
Also, I have a laptop and there is an integrated microphone but Linux doesnt seem to recognize it either. Thanks very much for your time and help.
:KS

---

### Post by stanca on 2009-10-07
sudo apt-get install subversion build-essential linux-headers-$(uname -r) && wget [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2) && tar xf tip.tar.bz2 && cd gspca-* && make && sudo make install && sudo depmod -ae $(uname -r) ;)

---


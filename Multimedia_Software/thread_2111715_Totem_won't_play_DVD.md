---
title: "Totem won't play DVD"
date: 2013-02-02
forum: Multimedia Software
---

### Post by Tom6153 on 2013-02-02
I have ubuntu 12.10 64bit 
i read the documentation for totem and it simply says that you insert the disk then open totem then click on movie and click play, i can click on movie but i can't click on play
i can only do open, open location and documentation
i have tried several dvds and it doesnt work

before i had ubuntu i had windows 8 readyinstalled

dont understand why its not working
please help

---

### Post by ajgreeny on 2013-02-02
Read these two carefully:-
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Tom6153 on 2013-02-03
thanks
i put vlc player in also and it works nicely

---

### Post by hicksrobin42 on 2014-01-16
Totem doesn't play DVD's because of a gstreamer bug that hasn't been fixed yet, the bug isn't present in 12.04. To play DVD's properly in 12.10 through 13.10 try using VLC until the bug is repaired.

---

### Post by fischerking2 on 2014-02-19
I'm running Ubuntu 13.10 64 bit and I've managed to get Totem working. Install the latest GStreamer plugins using the ppa.

Open up a terminal and add the repository:

sudo apt-add-repository ppa:gstreamer-developers/ppa

sudo apt-get update

sudo apt-get dist-upgrade

Then restart and Totem should play DVDs. This seems to fix the gstreamer bug.

---

### Post by Lei_Jiang on 2014-02-19
AFAIK playing back things with DRM has always been tricky on Linux. 

By DVD you mean the last generation D5/D9 DVD or the latest Blu-Ray DVD? I don't know any existing solution to play Blu-Ray directly on Linux. In fact the support is also very limited on OSX. If it's the old D5/D9, have you tried Xine? It worked for me pretty well quite a few years back. I presume it should not get worse these days.

---


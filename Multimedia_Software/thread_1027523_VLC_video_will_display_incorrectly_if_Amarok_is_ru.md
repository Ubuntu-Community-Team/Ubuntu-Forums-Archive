---
title: "VLC video will display incorrectly if Amarok is running"
date: 2009-01-01
forum: Multimedia Software
---

### Post by sproaty on 2009-01-01
If I have the Amarok application open, not even playing any songs (nor paused, simply "stopped") then if I watch a video in VLC then the video will start displaying random square blocks of black pixels. Closing Amarok fixes this.

I'm using 8.10 with the latest updates, 64 bit version. I've done a few google searches on the issue but can't find anything.

I have a Creative X-fi and the right drivers installed and an Nvidia 8800GT with the recommended 177.x drivers installed.

---

### Post by sproaty on 2009-01-01
Actually, I've narrowed it down to only happening if a track is paused. The screen will distort, as in the image below:

[[IMG]http://img119.imageshack.us/img119/231/vlcuv3.th.jpg[/IMG]](http://img119.imageshack.us/my.php?image=vlcuv3.jpg)

---

### Post by xc3RnbFO8P on 2009-01-01
Run VLC and Amarok in separate Terminal windows, see if it shows some errors.

---

### Post by sproaty on 2009-01-01
Running amarok from the terminal opens the program, but it returns me to the command prompt, whereas VLC will load and then display some output in the terminal

[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
steve@ubuntu:~$

---

### Post by xc3RnbFO8P on 2009-01-02
I got this (blinking chessboard) if I enable all the visual windows in Amarok.

---


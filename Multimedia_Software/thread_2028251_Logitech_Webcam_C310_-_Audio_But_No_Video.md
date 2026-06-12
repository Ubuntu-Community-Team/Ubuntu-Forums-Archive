---
title: "Logitech Webcam C310 - Audio But No Video"
date: 2012-07-17
forum: Multimedia Software
---

### Post by steve7777777 on 2012-07-17
Ubuntu NOT Lubuntu...

Webcam Logitech C310 - audio working but not video

steve@777777764V10:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.4 LTS
Release:	10.04
Codename:	lucid
steve@777777764V10:~$ lsusb
Bus 008 Device 002: ID 046d:081b Logitech, Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 004 Device 002: ID 05af:0408 Jing-Mold Enterprise Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

--

I tried with Cheese - no video, and then Skype - no audio/video. The green light on the webcam comes on. I selected the Logitech C310 since it should work right out of the box, lol.

Any suggestions?

---

### Post by steve7777777 on 2012-07-18
Solved - tried a different USB port and it works - video and audio no configuration needed. The USB port that resulted in failure may have been USB 3.0.

---


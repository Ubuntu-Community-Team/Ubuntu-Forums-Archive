---
title: "all movie players shutdown automatically"
date: 2010-01-19
forum: Multimedia Software
---

### Post by rshrty_15 on 2010-01-19
i have tried playing from movie player dragon player and VLC and when i do VLC in terminal i get this 

VLC media player 1.0.2 Goldeneye
[0x8533140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x89eb5c8] pulse audio output: No. of Audio Channels: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  110
  Current serial number in output stream:  111
Segmentation fault

someone tell me what up and i have checked for drivers shows me with no proprietary drivers

---

### Post by ryan83189 on 2010-01-20
I have this problem too. I'm sorry that i can't offer anymore help, I just wanted to say it so people don't suspect an isolated incident.

---

### Post by doas777 on 2010-01-20
yeah the problem definetly seems to be the lack of a compatible vid card/driver. what kinda card do you have?

---

### Post by ryan83189 on 2010-01-20
A workaround that worked for me is in this thread

[http://ubuntuforums.org/showthread.php?t=1386484](http://ubuntuforums.org/showthread.php?t=1386484)

hope it helps

---

### Post by 12_String on 2010-01-20
I have a similar problem, no videos play, just a black box with an arrow in a circle and the controls.

---


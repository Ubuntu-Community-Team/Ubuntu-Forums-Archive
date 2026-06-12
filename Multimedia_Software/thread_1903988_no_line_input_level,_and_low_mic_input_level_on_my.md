---
title: "no line input level, and low mic input level on my gateway laptop"
date: 2012-01-03
forum: Multimedia Software
---

### Post by kerneloflove on 2012-01-03
HI I'm pretty much a beginner with unbuntu.

I'm not getting any level coming through my line input/external mic input
I've tried cycling through all my options in ALSA mixer and pavucontrol.

I get input from the internal mic, although that is lower than I like and I have not been able to increase that.

Any ideas?

---

### Post by lidex on 2012-01-04
> **kerneloflove said:**
> HI I'm pretty much a beginner with unbuntu.

I'm not getting any level coming through my line input/external mic input
I've tried cycling through all my options in ALSA mixer and pavucontrol.

I get input from the internal mic, although that is lower than I like and I have not been able to increase that.

Any ideas?

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by kerneloflove on 2012-01-04
K>O>
[http://www.alsa-project.org/db/?f=c07cb7102bbfbe1e162f0cb82af90bd127cb3e73](http://www.alsa-project.org/db/?f=c07cb7102bbfbe1e162f0cb82af90bd127cb3e73)

---

### Post by kyosaku on 2012-01-15
Hello there, I can confirm having this problem.  Sound recording on my ubuntu 11.10 has been working fine until just recently.  The problem is exactly the same as described, no more recording signal from line in, and very low microphone. Sound can be played normally through speakers, though.  When I use Skype with USB  phone sound recording is alright.  In XP everything works fine.

ALSA log file  [http://www.alsa-project.org/db/?f=7ddf66ad93e3d4a4150447b712b7672c507bca72](http://www.alsa-project.org/db/?f=7ddf66ad93e3d4a4150447b712b7672c507bca72)

---

### Post by kyosaku on 2012-01-15
In the meantime ...
I was able to solve my problem by installing PulseAudio Volume Control, enabling "Monitor of Line In" on its Input Devices tab (after making sure all input devices are shown).  :D

  thanks to **[anhe51's blog]("http://anhe51.wordpress.com/")**

[http://anhe51.wordpress.com/2012/01/13/record-youtube-with-audacity-on-ubuntu-11-10/](http://anhe51.wordpress.com/2012/01/13/record-youtube-with-audacity-on-ubuntu-11-10/)

still do not know why this thing stopped working all of a sudden.  didn't need pulseAudio volume control before ..
hope this helps you as it helped me !

---


---
title: "After ALSA tweak, no sound at all."
date: 2008-10-29
forum: Multimedia Software
---

### Post by LOTM on 2008-10-29
So, being a Linux noob, I found it strange that it seemed only one program could output audio at a time, so yesterday, I was checking on the forums and found the Comprehensive Sound Problem Solutions Guide, and followed its directions for installing and configuring ALSA drivers for my computer. After going through the first part of the guide, I followed the direction and tried to compile ALSA with module-assistant, but it kept erroring. I the read the rest of the hints and found the section on how to get more than one application to use the sound card at a time. After following those directions, I was able to use the aoss command to launch the programs , and get them to play music, etc. However, problems began when Ubuntu updated yesterday. After the computer restarted following the update, no programs could output audio. I tried the aoss command and while it says it's playing, I get no sound. Does anyone have any ideas?

---

### Post by ajgreeny on 2008-10-29
It is probably the fault of the new kernel which arrived with yesterday's updates, and you may need to go through the palaver of installing the alsa drivers etc that you did last time.  This tends to be the problem with new kernels when you have added drivers to them yourself.  You could try booting to the 2.6.24-19 kernel if you have it, or even the 2.6.24-16 which was the kernel originally installed with hardy.

---

### Post by LOTM on 2008-10-29
Ok, thanks. I'll probably just end up realoding Ubuntu entirely, since there are some other things that I have messed up.

---

### Post by markbuntu on 2008-10-29
If you do reinstall, go here first to get your sound working. At the least get all the packages listed there.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---


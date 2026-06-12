---
title: "Software Audio Amplifier"
date: 2008-10-02
forum: Multimedia Software
---

### Post by T3h_Dohtem on 2008-10-02
I have been having some problems hearing audio on my Ubuntu laptop. I have the volume cranked up everywhere possible, the mixer settings, the hardware volume control, and whatever player is currently in use, and still any audio is barely...well, audible. I was hoping somebody could point me to a software amplifier? I'm not sure if any such thing exists, but I know the integrated speakers on my system are capable of much more volume, if I can only get it cranked up to them. Thanks in advance for any pointers.

---

### Post by Bungo Pony on 2008-10-02
I normally have problems with too much audio, and everything ends up distorted.

Try going into a terminal and typing alsamixer. You'll find various audio controls there. Try increasing the master volume.

---

### Post by markbuntu on 2008-10-03
This guide has helped many people with your particular problem:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by T3h_Dohtem on 2008-10-04
My mixer settings are already maxed, (ie. alsamixer is cranked all the way up) but I will check into that link Markbuntu. I browsed it so far and looks like the EQ may be helpful. Thanks for the ideas, and thanks in advance for any further suggestions.

---

### Post by ethana2 on 2008-11-08
The fact of the matter is that the way Ubuntu handles volume is seriously flawed.

It needs to be in decibels, and it needs to have a good positive range.
Alternately, it should go from 0 to 200%, not just 100%.

---


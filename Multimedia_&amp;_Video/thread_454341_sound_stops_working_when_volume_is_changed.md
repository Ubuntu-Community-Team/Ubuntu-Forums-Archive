---
title: "sound stops working when volume is changed"
date: 2007-05-25
forum: Multimedia &amp; Video
---

### Post by bford16 on 2007-05-25
I just did a fresh install of ubuntu feisty 7.04, on an ASUS motherboard.  The soundcard is a via vt82xx, using the alsa mixer.

When I start the computer, sound works fine.  If I play some music, no problem.  If I change the volume, BAM! no sound until I restart ubuntu.  Then the sound comes back.  Help!

---

### Post by dabl on 2007-05-25
Did you have your browser running when the sound stopped?  I noticed a funny thing on my Feisty 64-bit installation -- I can play sound files with Audacity and no Firefox, but if I run Firefox then Audacity won't produce sound -- it looks like it is "playing" the file, but nada from the speakers.

---

### Post by bford16 on 2007-05-27
Yes, but that was not the problem.  Apparently Ubuntu switched to a [nonexistant] sound card when I hit the volume control.  The solution was to add the following to /etc/modprobe.d/alsa-base:
options snd-hda-intel position_fix=1 model=3stack

I did that, and now, no problem.  I found the solution in <http://ubuntuforums.org/showthread.php?p=1521207#post1521207>

---

### Post by bford16 on 2007-06-19
> **bford16 said:**
> Yes, but that was not the problem.  Apparently Ubuntu switched to a [nonexistant] sound card when I hit the volume control.  The solution was to add the following to /etc/modprobe.d/alsa-base:
options snd-hda-intel position_fix=1 model=3stack

I did that, and now, no problem.  I found the solution in <http://ubuntuforums.org/showthread.php?p=1521207#post1521207>

UPDATE: this solution also worked on openSUSE 10.2, but with a slight difference.  Instead of entering the "position_fix=1 model=3stack" in /etc/modprobe.d/alsa-base, I entered it in /etc/modprobe.d/sound.  Also, there is a strange new twist: apparently the volume control is shared between PCM and Front.  I must have at least some volume in each to get full volume.  

And there is the high-pitched tone that my wife and kids say is very annoying. I of course cannot hear it...

---


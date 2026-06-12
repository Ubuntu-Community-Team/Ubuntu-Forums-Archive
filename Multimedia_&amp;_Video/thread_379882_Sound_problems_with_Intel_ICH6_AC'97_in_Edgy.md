---
title: "Sound problems with Intel ICH6 AC'97 in Edgy"
date: 2007-03-09
forum: Multimedia &amp; Video
---

### Post by doc zein on 2007-03-09
I've been using Ubuntu for a while but the sound is the only thing that's keeping from erasing my Windows partition. I have a Shuttle computer, which are those mini-computer type systems. Ubuntu lists my sound card as an Intel ICH6 (Alsa mixer). First of all, I can't get sound to work across multiple applications. If i play a sound in Songbird, I can't hear sounds in Gaim, etc. I've tried going into System>Preferences>Sound and setting them all to ALSA, or OSS, or ESD, but nothing works. I can only have one application playing sound at a time. Additionally, when I play flash videos, the sound always seems to be "popping" or "crackling". If i watch flash videos for a while i start to not mind it but it really is annoying. I use 5.1 surround sound. Anyone know the problem?

---

### Post by doc zein on 2007-03-09
help? anyone?

---

### Post by drpaul on 2007-03-09
Have you tried installing a more up-to-date version of the alsa driver? I'm not familiar with your hardware, but I've seen that resolve sound problems for many users.

HTH

Paul

---

### Post by doc zein on 2007-03-10
i've tried installing the most up-to-date version using module-assistant, but it fails to successfully build the alsa driver and does not reach 100%.

in addition, i've taking doing a sudo make install with the alsa-driver1.0.13 from alsa-project, but this seems to do absolutely nothing. in the package manager it still lists the latest version of alsa as 1.0.11.

---

### Post by drpaul on 2007-03-10
Did you reboot after make install?

Did you add snd-hda-intel to the end of the modules file?

Paul

---

### Post by doc zein on 2007-03-10
yes, i have done both, but it doesn't seem like the alsa driver is updating, and everything is the same as before.

---

### Post by doc zein on 2007-03-14
help? anyone?

---

### Post by Levenly on 2007-03-15
Doc, I'm not sure if you've seen this page before but this guy had the same audio controller as you did, but had no sound at all.

[http://ubuntuforums.org/showthread.php?t=120070](http://ubuntuforums.org/showthread.php?t=120070)

Also, Alsa has some .pdf file about your controller (Adobe isn't working for me so I'm not sure what it's about)

[http://www.alsa-project.org/alsa/ftp/datasheets/intel/30234902_ICH6.pdf](http://www.alsa-project.org/alsa/ftp/datasheets/intel/30234902_ICH6.pdf)

You could possibly try removing OSS completely- maybe it's interfering too much with ALSA.

sudo dpkg --remove --force-depends --force-remove-reinstreq oss-linux

[http://ubuntuforums.org/showthread.php?t=34860](http://ubuntuforums.org/showthread.php?t=34860)

Just trying to help ya bud :) .

Let me know if you've already gone through these things or if any of them didn't work- I can dig deeper through these forums.

Worst case scenario is you have to reinstall Ubuntu, or install another distribution of Linux.

---

### Post by gtn130 on 2007-03-15
Doc Zein, If you cannot resolve your sound problem, we'll bury the whole thing. We will bury the hatchet. :|

---

### Post by Levenly on 2007-03-16
Look here Doc.  I don't appreciate your responsiveness to your **own** thread.  If you don't want my help then fine.  I suggest you do some soul searching man...  your attitude reflects that of an in-season Lacrosse player.

---

### Post by feerlessleadr on 2007-08-03
Hi, I'm sorry to bump such an old thread but I am having this exact same problem.

I have updated the alsa driver to its latest version (1.0.14rc3) or at least i think that is the latest version.

I also looked through the other 2 links that you posted and nothing goin for me.

Also I'm pretty new to linux so please be gentle :(

Just some background...my sound was working but i updated Ubuntu (feisty) and then all of a sudden my sound stopped working. Thanks in advance.

---

### Post by feerlessleadr on 2007-08-06
anyone?

---


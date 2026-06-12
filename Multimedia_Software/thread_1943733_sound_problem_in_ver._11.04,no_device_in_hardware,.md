---
title: "sound problem in ver. 11.04,no device in hardware,output= dummy output"
date: 2012-03-20
forum: Multimedia Software
---

### Post by deewakar on 2012-03-20
I'm pretty new to Ubuntu. I installed it a few days ago alongside my Windows installation . Everything worked fine until I installed drivers package of Realtek audio for linux(which I later found was ALSA drivers).I didn't know then what was ALSA ,so I installed it but it didn't installed properly. It was complaining something about not being able to  create or delete some files which I don't remember now (and which I didn't thought was important at the time since I had my previous drivers which was already installed when Ubuntu was installed). Then I installed flash plugin and when I tried to watch some video on youtube, No Sound!. Then I remembered that while installing alsa drivers it had thrown a warning that after installation of alsa drivers I would have to unmute the sound from alsa mixer. So for some reason I opened 'Sound Preferences' and there you go no devices in Hardware section ,no devices in input and "Dummy Output" in the output section.
Damn! I was panicking . What do I do! What do I do!(don't blame me, it's natural for Windows users)
I tried every step from the sticky help ( both of them), but still "Dummy output".I totally removed alsa drivers
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```and re installed it.
```
  sudo apt-get install linux-sound-base alsa-base alsa-utils 
```but still dummy output.
Here's a link to my alsa diagnostic script results: [http://www.alsa-project.org/db/?f=6e55e93a51dc5b163fab68e86c0203ea1abede16](http://www.alsa-project.org/db/?f=6e55e93a51dc5b163fab68e86c0203ea1abede16)
 I've tried everything that was possible in one whole day. Now I'll puke if I see any of the words like "ALSA" or "Dummy Output" or "hda-intel" .Man! what do I do now.

---

### Post by deewakar on 2012-03-21
I fixed it myself by using the script given in the below thread:
[http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

The problem was my kernel was updated to 2.6.38-13 but my ALSA modules were not.

---


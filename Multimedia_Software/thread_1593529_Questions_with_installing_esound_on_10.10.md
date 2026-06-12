---
title: "Questions with installing esound on 10.10"
date: 2010-10-11
forum: Multimedia Software
---

### Post by Pharod on 2010-10-11
I recently installed Quake 3 and Wolfenstein: Enemy Territory, and after reading a lot on making the sound work, I found a great resource [here]("https://help.ubuntu.com/community/EnemyTerritory").

The thing is that when I try some of the solutions this is what happens:
[LIST=1]
[*]When using apt-get install esound, the package manager wants to remove pulseaudio-esound-compat & ubuntu-desktop.
[*]When using apt-get install libsdl1.2debian-alsa, the package manager wants to remove libsdl1.2debian-pulseaudio & ubuntu-desktop
[/LIST]

The sound is working flawlessly except for those two games, and I'm not sure if removing those packages (especially ubuntu-desktop) will make a mess. So I guess my question is What will be the impact of removing those packages? To rollback the system I just remove the new packages and install the old ones?

Thank you for your help!

---

### Post by kotnik on 2010-10-16
You can try to remove ubuntu-desktop, I don't think that you'll have problems, but YMMV.

The reason sound desn't work in those games can be traced to this (I'd say stupid) decision on Ubuntu side: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579300](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579300).

---

### Post by Yellow Pasque on 2010-10-16
These games use opneal, which can output directly to pulse. It should be the default, but if not, edit /etc/openal/alsoft.conf and uncomment the driver line with pulse being the first choice.

---

### Post by kotnik on 2010-10-17
The solution for ET: [http://nullkey.ath.cx/~stuff/et-sdl-sound/](http://nullkey.ath.cx/~stuff/et-sdl-sound/)

Follow the first method under 'install', and sound in ET should be working without problems.

---


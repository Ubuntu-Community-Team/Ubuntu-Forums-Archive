---
title: "HP DV4-2014 Videos without sound and master volume control don't works"
date: 2010-01-03
forum: Multimedia Software
---

### Post by robertoaguiarlima on 2010-01-03
I buy a HP DV4-2014 laptop, and have some troubles with sound.
Initialy sound only works with headsets pluged. Then I install the package linux-backports-modules-alsa-karmic-generic, so speakers works fine whithout head sets.
The worst problems that yet is occurring is videos without sound. Using Totem none video works, and audio files too. For exemple /usr/share/example-content/Ubuntu_Free_Culture_Showcase/InTheCircle.oga don't works. Curiously it functions with rhythmbox. Flash player inside fire fox too don't play sound, for exemple videos in [www.youtube.com](www.youtube.com) plays without sound.
I already read various threads about it in the forum, but no one works to.
I already checked volume controls and installed gstreamer plugins.
thanks a lot!

---

### Post by robertoaguiarlima on 2010-01-03
I reinstaled the ubuntu I used the 9.10 Karmic amd_64

The steps are:
1 - install ubuntu by CD
2 - In the first run of ubuntu, after instalation, I instal the package linux-backports-modules-karmic-generic.
3 - boot ubuntu after package instalation
4 - Next I instaled the package linux-backports-modules-alsa-karmic-generic
5 - boot. In this steps the master volume control is working and videos are working too.

The sound is working fine and the audio of videos too. I don't know why this is working now, but I am glad!

---

### Post by robertoaguiarlima on 2010-01-07
After one of ubuntu updates my microphone and headsets stop to work. 
The solutio for this was:
1 - Give the command (alt+f2 in gnome): gksudo gedit /etc/modprobe.d/alsa-base.conf
2 - Go to the last line and put a new line like this: options snd-hda-intel model=auto
3 - Reboot.

---


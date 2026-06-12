---
title: "sound pops on reboot"
date: 2010-08-27
forum: Multimedia Software
---

### Post by fjskmdl on 2010-08-27
Just as in this thread:
[https://bbs.archlinux.org/viewtopic.php?pid=811758]("https://bbs.archlinux.org/viewtopic.php?pid=811758") my sound pops on reboot/shutdown

the suggested solution is to add the following lines to /etc/rc.d/alsa:

amixer set Master mute >/dev/null
modprobe -r snd-hda-intel

but i don't have /etc/rc.d/alsa
I use a standard ubuntu 10.04 installation. (so i guess i use pulseaudio)

In general, my question is how i can mute the master channel and unload the snd-hda-intel module before reboot/shutdown.

---


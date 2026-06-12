---
title: "No front R/L sound from 5.1 Xonar D1"
date: 2013-02-15
forum: Multimedia Software
---

### Post by biggio75 on 2013-02-15
Hi everybody!

I have this problem. During 2 years i used a xbmc mediacenter system with ubuntu 11.04 64bit. My mediacenter has an Asus Xonar D1 audio card connected to a homemade amplifier. Near the ubuntu os i have installed windows 7 to see the blu-ray movies.
Two days ago i have decided to upgrade my system to ubuntu 12.10. Then to make evething better i formated the ubuntu partition to a new one. I installed everything and all works fine like before except the sound card. 
On the 5.1 system i hear only the two rear r/l, the center and the sobwoofer, but not the two front r/l. 
I tried to solve the problem changing the /etc/pulse/daemon.conf, raising the volume on alsamixer and following this guide:

[https://help.ubuntu.com/community/DigitalAC-3Pulseaudio](https://help.ubuntu.com/community/DigitalAC-3Pulseaudio)

But nothing, the two front r/l don't want to work!
I want to point out that on windows partition all works fine.
Please help me!!!

---

### Post by Yellow Pasque on 2013-02-15
You should probably file a bug. I suggest making sure that you have your configuration files as close to stock as possible (for example, reinstall pulseaudio package to  reverse any changes you made to /etc/pulse/daemon.conf ).
This command should do it:
```
ubuntu-bug alsa-base
```
Once you have the bug link, make a verbose pulse log and post/attach it on the bug report: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---


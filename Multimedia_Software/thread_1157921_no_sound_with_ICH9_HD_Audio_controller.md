---
title: "no sound with ICH9 HD Audio controller"
date: 2009-05-13
forum: Multimedia Software
---

### Post by bob227 on 2009-05-13
Hi

I installed Ubuntu 9.04 on my HP 6830s mobile but can't get any sound (system or application). I am new to ubuntu by already tried several things to solve this problem. I know that my soundcard is correctly installed(aplay -l and lspci) and not muted. I haven't got a lineout so the sound can't be directed to the external amplifiers. I reinstalled the alsa drivers with the purge option to eliminate the old configuration. I ran the alsa information script which confirms that my soundcard is correctly installed and recognized. It also says that pulseaudio is installed and running.
(URL of the infofile: [http://www.alsa-project.org/db/?f=a049ffc82506a5e7db315b2f3e3cd505e228099b](http://www.alsa-project.org/db/?f=a049ffc82506a5e7db315b2f3e3cd505e228099b))

I suspect that my soundcard isn't correctly supported by alsa:
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
I would be really grateful if somebody could help me with this problem.

bob

---

### Post by bob227 on 2009-05-13
I wanted to add that I have access to sound in Ubuntu
[SIZE=2]grep 'audio' /etc/group

[/SIZE]returns:
audio:x:29:pulse,bob,root

---


---
title: "No audio - have driver, both alsa and pulseaudio"
date: 2009-07-18
forum: Multimedia Software
---

### Post by bwooster47 on 2009-07-18
Keep getting the KDE notification "playback audio device HDA Nvidia ALC622 Analog" does not work, falling back to .
speaker-test -Dplughw:0,0 -c2 says:
Playback open error: -16,Device or resource busy

Did a fresh install of Kubuntu 9.04 - could it be that x86_64 is the problem here?

Linux ... 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

Followed two of the threads as much as I could:
[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)  KDE4/Phonon
[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384) Jaunty 9.04 Sound Solutions

No luck - aplay -l seems fine:
card 0: NVidia [HDA NVidia], device 0: ALC662 Analog [ALC662 Analog] ....
lspci shows:
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)

Then installed pulseaudio and related tools, now the KDE notification
says same message, adding "falling back to pulseaudio".

Syslog shows similar message:
alsa-util.c: Error opening PCM device hw:0: Device or resource busy
and then Failed to load  module "module-alsa-sink" and later module-alsa-source.

Looked at various mixers, all look fine, don't see anything muted. There is no sound on reboot also.

---

### Post by igorzwx on 2009-07-18
try oss4

---


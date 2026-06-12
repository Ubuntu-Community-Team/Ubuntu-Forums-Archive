---
title: "Trying a different way to get a system EQ..."
date: 2009-08-19
forum: Multimedia Software
---

### Post by greatman05 on 2009-08-19
Hello. I followed the tutorial [here]("http://wiki.archlinux.org/index.php/ALSA#System-Wide_Equalizer") to try to get Ubuntu to have a system equalizer. The problem is that the settings have no effect. I've tried restarting ALSA and restarting Ubuntu, but neither option works. I have an .asoundconf file in my home folder, and asound.conf in my /etc folder, so what's the problem? 

P.S.: I did the PulseAudio tutorial for system-wide EQ, but it uses too much CPU since it's not really supported on Jaunty, the version I am running. Also, I'm running this distribution on a 2GB flash drive made with Ubuntu Live USB Maker 0.2.

P.S.S: Just found out that system sounds won't play through the "Sound" control applet, and the command "aplay -Dplug:eq /usr/share/sounds/question.wav" returns this error:

ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM eq
aplay: main:590: audio open error: File exists

I'm including my ALSA config files in an attachment.

---


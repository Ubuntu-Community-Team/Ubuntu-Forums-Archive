---
title: "Pulseaudio server refuses to connect"
date: 2017-11-03
forum: Multimedia Software
---

### Post by andrewdrz on 2017-11-03
Dear all, I'm running kubuntu 17.10 and after ~4 days after clean installation of this system, pulseaudio server crashes and refuses to connect (obviously, daemon startup failed). It should be noted that I had same problem, when I was running ubuntu 17.04 with KDE 5. 

I've tried the next sequence of steps:
1) purge and reinstall pulseaudio, pavucontrol-qt, plasma-pa, pulseaudio modules (bluetooth, gconf)
2) reboot
3) alsa force-reload
4) launch pavucontrol-qt
Everything worked until next reboot. 

What am I doing wrong?

I've tried to run pulseaudio --check, but it gave me nothing
[FONT=monospace][COLOR=#000000] 
Then
ps auxw | grep pulse 
Gives me 
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]andrew    9218  0.0  0.0  15836  1176 pts/1    S+   08:20   0:00 grep --color=auto [/COLOR][COLOR=#FF5454]**pulse**[/COLOR]
[/FONT][FONT=monospace]
Any thoughts? [/FONT]

---

### Post by Yellow Pasque on 2017-11-03
1. Try getting a log: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)
2. You can also try clearing user pulse configuration:
```
rm -r ~/.pulse
```

---

### Post by andrewdrz on 2017-11-08
Finally, I've caught this problem. The problem was in the pulseaudio-module-gconf. 
**SOLUTION:**
I've re-installed pulseaudio, plasma-pa, pulseaudio-module-bluetooth and kmix. After this I removed **pulseaudio-module-gconf, **&#8203;rebooted my device and everything worked fine.

---


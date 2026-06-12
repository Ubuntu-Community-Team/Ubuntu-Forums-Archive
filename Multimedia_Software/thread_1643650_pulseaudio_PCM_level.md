---
title: "pulseaudio PCM level?"
date: 2010-12-12
forum: Multimedia Software
---

### Post by pickarooney on 2010-12-12
I've always used Xubuntu up to now so never experienced pulseaudio really. When I tried to upgrade to Maverick I found out the CD was corrupt only after the partitioning/formatting stage so I had to use a Ubuntu CD and install from there then install xubuntu-desktop.

So now I have Maverick in XFCE but on a Ubuntu base install and pulseaudio is running. It seems to be working OK so I'll leave it for now but I can't figure out how to adjust the PCM audio level, or in fact any other audio level - I just have one slider available, for master audio. Is there something I can install or run to be able to set the various audio properties one by one (PC speaker, Mic, mic boost, PCM, etc.) ?

---

### Post by ajgreeny on 2010-12-12
Run ```
alsamixer
``` in terminal and check that the levels of outputs are not set too low.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

---

### Post by pickarooney on 2010-12-12
Great, thanks! I'd tried about 5 mixers but never thought of the old console-based alsamixer :)

---

### Post by BcRich on 2010-12-12
hi pickarooney
if you havn't already tried it and want a GUI, PulseAudio Volume Control (referred to as pavucontrol in repos) is a great pulse audio mixer :)

---


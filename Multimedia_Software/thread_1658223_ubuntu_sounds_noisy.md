---
title: "ubuntu sounds noisy"
date: 2011-01-02
forum: Multimedia Software
---

### Post by cyb3rman on 2011-01-02
at a time, my music on ubuntu sounds noisy and rustling.
i know that it's from ubuntu because in windows the sounds are clear and played correctly.
i tried different media players and even on youtube i have this problem

what should i do?

---

### Post by lidex on 2011-01-02
Hard to say from that description. Have you checked your levels in alsamixer?
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

No joy? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---


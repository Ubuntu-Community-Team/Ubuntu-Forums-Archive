---
title: "problem with mic[s] in Ubuntu 11.04"
date: 2011-08-19
forum: Multimedia Software
---

### Post by Ghorab on 2011-08-19
welcome,
I have a computer (DELL OptiPlex 745) with built-in sound card.
but when i want to connect a mic he doesn't work.
i try USB and 3.5 mm jack mic, both don't work.
and i'm sure the mic unmute.
when i try it with Sound recorder i got noise such as shshshsshshshshshshsh

---

### Post by lidex on 2011-08-20
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Ghorab on 2011-08-20
hello Lidex,
i follow your reply and i got this message
> Your ALSA information is located at [http://www.alsa-project.org/db/?f=a09e28b2943ab9a83e89a325f538219fe4239e2f](http://www.alsa-project.org/db/?f=a09e28b2943ab9a83e89a325f538219fe4239e2f)


---

### Post by lidex on 2011-08-22
> **Ghorab said:**
> hello Lidex,
i follow your reply and i got this message

This indicates the mic channel is muted:
```
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 31
  Mono: Capture [on]
  Front Left: Playback 30 [97%] [10.50dB] [off]
  Front Right: Playback 30 [97%] [10.50dB] [off]
```

**Alsamixer**
Using a Terminal
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

Unmute mic 0

---


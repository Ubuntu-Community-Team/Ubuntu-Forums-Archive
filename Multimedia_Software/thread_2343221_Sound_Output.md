---
title: "Sound Output"
date: 2016-11-14
forum: Multimedia Software
---

### Post by Billisnice on 2016-11-14
I have sound out 1) puter and 2) USB sound device. The only options are Built in Audio and my other device not both to use. Anyway to get both sound devices working at the same time?

!) Built in Audio
2) CM-108 Audio Controller

---

### Post by yetimon_64 on 2016-11-14
In pulseaudio preferences there is a "Simultaneous Output" tab. When the box is ticked on it you are then given a virtual output device in the pulseaudio volume control window you can choose to use to use both devices at the same time. See attached screenshot. 

You may possibly need to add pulseaudio preferences, I am not sure if it is on a standard install, you can check if you have it with the next command ...
```
apt-cache policy paprefs
```If not installed you can easily add paprefs with the "sudo apt-get install paprefs" command (without the quotes).

---

### Post by slickymaster on 2016-11-14
*Thread moved to **Multimedia Software**.*

---

### Post by Billisnice on 2016-11-14
When i tick the add virtual output it does nothing...thanks   It worked! I did a reboot of puter...Thanks

---


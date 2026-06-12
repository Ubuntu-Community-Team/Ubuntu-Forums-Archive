---
title: "Fresh Install No Sound"
date: 2011-06-29
forum: Multimedia Software
---

### Post by Ivor Grumble on 2011-06-29
I've searched all day long, on here, on Google, no one comes up with a definitive answer. I've tried millions of things, installed this app and that thing according to advice to people with the same problem, still no sound. 

My sound was working fine when I was trying out Ubuntu on a partition, I was so chuffed with it I did a fresh install. I have no sound. VLC, Amarok, Clementine, Audacity, Audacious, every audio player in the Ubuntu Universe doesn't play sound. Obviously it's something 'hardware' or 'driver' connected because it all worked perfectly when I still had Windows as the 'host' partition. I'm not going back to Windows I'll try out OpenSuse or something to see if the sound thing happens on that.

Please don't direct me to another thread so that I can read another ten million words which don't help in the end, or ask me to see if the 'mute' button is on. Is there a test thing out there that finds and corrects or at least points me in the right direction. I don't want to be 'trying this or that solution' for another 9 hours.

---

### Post by dabl on 2011-06-29
> **Ivor Grumble said:**
> 

My sound was working fine when I was trying out Ubuntu on a partition

One approach would be to find out what sound module(s) are loaded when it plays sound with a Live CD (use lsmod to see the loaded modules).  Then you want to make sure that same module is loaded when you boot your installed system.

Another approach might be to actually tell us what sound chip you have there, so someone else can look it up for you on the ALSA project web site.

(lspci -vv will show it)

---

### Post by lidex on 2011-06-30
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---


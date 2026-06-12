---
title: "Microphone problem in easynote  TJ61"
date: 2011-02-27
forum: Multimedia Software
---

### Post by leguitos on 2011-02-27
I've been having this problem for a while and been googling to try to find a solution.

I fond this post that may sort me out but i don't know how to open the file and edit it... Can u guys help me?

matricks
November 15th, 2009, 05:11 AM

Just  bought a laptop Packard Bell Easynote TJ61 with an internal sound card  Conexant CX20561 (Hermosa) and successfully installed Ubuntu 9.10  64-bit. Only problem was that the microphone (internal and external) was  not working in all applications (soundrecorder, audacity, skype etc).  Output audio (eg- Rythmbox) worked fine with ALSA and PulseAudio. 
Tried a LOT of stuff, but the decisive move was to add: 
options snd-hda-intel position_fix=1 model=laptop
to the file /etc/modprobe.d/alsa-base.conf and reboot.
If hope this helps ... Another thread dealing with the Conexant chip  microphone is read-only otherwise I would have posted there.



Thanks

---

### Post by cchhrriiss121212 on 2011-02-27
First, open the terminal from the accessories menu. This is a system file so you will need the sudo command to edit it:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
Then just copy and paste that line in at the bottom, save and reboot.

---

### Post by leguitos on 2011-02-28
Victory!!!!
Thx guys, u were most helpful :)
I now, have my computer fully compatible with ubuntu :):):)

---


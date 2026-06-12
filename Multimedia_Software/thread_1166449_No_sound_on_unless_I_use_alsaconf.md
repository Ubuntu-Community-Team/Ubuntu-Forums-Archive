---
title: "No sound on unless I use alsaconf"
date: 2009-05-21
forum: Multimedia Software
---

### Post by marshmallow1304 on 2009-05-21
I'm running a minimal install of Jaunty with LXDE.
The sound card is a Yamaha OPL3-SA2.

After I start up, I have no sound, even if I do
```
modprobe snd-opl3sa2
```
I have also made the entry in /etc/modules.

Running alsaconf clears it right up, but I'd rather not have to do that every time.

---

### Post by marshmallow1304 on 2009-06-10
More info:

I've figured out that alsaconf fixed the problem because it sets the volume levels.  The problem now is that I can't get the volume levels to stay put (after a reboot, they go back to 0).

---

### Post by marshmallow1304 on 2009-06-20
bump

---

### Post by Drk Guy on 2009-07-04
Hey, how'd you use alsaconf? it aint on my system (kubuntu jaunty) and no packge relates to it that it's not installed :S

---

### Post by marshmallow1304 on 2009-07-07
> **Drk Guy said:**
> Hey, how'd you use alsaconf? it aint on my system (kubuntu jaunty) and no packge relates to it that it's not installed :S

If I remember correctly, I compiled alsa-utils from source.



Edit:  The machine in question is now a server, so the question is moot.

---


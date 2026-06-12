---
title: "Ubuntu Movie Player issue."
date: 2008-11-09
forum: Multimedia Software
---

### Post by CMR_98823 on 2008-11-09
Every time I try to open a movie file, it'll open the player, then close the app...someone out there's had a similar issue I'm sure, so anyone that can help, please by all means! :)


It seems to be doing this with VLC as well...


Seems to work fine in Xubuntu...any reason it wouldn't in Ubuntu?

---

### Post by CMR_98823 on 2008-11-10
I seem to be having problems with Rhythm Box now too...any time I try to place a song it freezes up on me...please help me :)

---

### Post by psyke83 on 2008-11-10
> **CMR_98823 said:**
> Every time I try to open a movie file, it'll open the player, then close the app...someone out there's had a similar issue I'm sure, so anyone that can help, please by all means! :)


It seems to be doing this with VLC as well...


Seems to work fine in Xubuntu...any reason it wouldn't in Ubuntu?

You're not giving enough information for anyone to realistically help. What version of Ubuntu? What graphics card and driver? With or without compiz?

It's a long shot, but you could be suffering from a variation of the X11 "BadAlloc" error (it used to occur for my Intel graphics before the driver switched to EXA acceleration).

See here (or any bugs dealing with BadAlloc errors, if you see it in the player output): [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/111257](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/111257)

---

### Post by CMR_98823 on 2008-11-10
Apologies for not specifying enough.

Ubuntu 8.10, Video card ATI x700 Pro, driver is FGLRX. Compiz is enabled.

Video works fine now, after some tweaking, however I am getting some sound, or no sound. In a movie file, the sound seems to skip and spatter. I can't play any music for some reason anymore...it was working flawlessly earlier.

Let me know if you need more info. Thanks!

---


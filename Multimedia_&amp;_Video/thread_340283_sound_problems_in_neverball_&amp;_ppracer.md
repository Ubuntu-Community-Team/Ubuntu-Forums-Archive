---
title: "sound problems in neverball &amp; ppracer"
date: 2007-01-17
forum: Multimedia &amp; Video
---

### Post by Yaks Hairbrush on 2007-01-17
Problem:

When I try to run Neverball or Planet Penguin Racer from a terminal, I get the error message 
```

open /dev/sequencer: No such file or directory

```
The games both work fine, except for the sound issue. A quick look in the /dev directory revealed that /dev/sequencer is indeed missing.

Other than these two programs, the sound works great. I have sound from the CD player, at startup, at shutdown, and in Warcraft 3 under wine.

Possible cause of problem:

I used the script at [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo) to install Qemu 0.8.2, and found that this script resulted in a qemu which produced hard crashes. I then uninstalled it through synaptic, and reinstalled qemu 0.8.0-ubuntu3. I suspect this caused the problem because I haven't done anything else drastic enough to cause the sound to fail.

Technical info:

I am running Ubuntu 64-bit Dapper.

Thanks in advance for your help.

---


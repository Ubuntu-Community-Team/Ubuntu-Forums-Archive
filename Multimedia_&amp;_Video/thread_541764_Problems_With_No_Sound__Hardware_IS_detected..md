---
title: "Problems With No Sound | Hardware IS detected."
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by matt-daemon on 2007-09-03
Just to let people know that i had the problem of no sound, however my hardware was detected.

In case of the new people that have just install ubuntu, like myself, If you do not have any sound. The most likly option is that the build of Alsa that came with ubuntu does not work, Simply Configure Rebuild install and restart.

This should then work fine.


nb.
I am using realtek AC97 HD On AMD64 Running Ubuntu 7.04

---

### Post by renzokuken on 2007-09-03
thats the same chipset i had.

edgy/feisty both come with alsa-driver 1.0.12 which dont support this chipset.

alsa-driver 1.0.14 **does**, so as matt-daemon says, compile the latest alsa-driver from source

---


---
title: "XMMS IRman"
date: 2007-03-26
forum: Multimedia &amp; Video
---

### Post by the.unclean.cpp on 2007-03-26
Hi! I have a Winfast TV 2000XP deLuxe edition Tv Tuner. I have a Remote control for it. It's detected by the system because I can change the system volume. However, I don't know in which device it's registered. I activated the IRman plugin and tried to set the keys but when I press a button, no signal is detected. Can it be registered in the same /dev place as the TV Tuner? And if not, how can I find out? If you have similar TV Tuners please tell me where is the Remote Control registered.
THanks.

P.S.: The IRman autosets the device at /dev/ttyS1 .

---

### Post by the.unclean.cpp on 2007-03-27
Nobody wants to answer? :(

---

### Post by racmar on 2007-06-21
for me, irman /w lirc has been broken in feisty.  I've downgraded lirc to 0.8.0-5ubuntu-1 from edgy.  I have tried a few times to get irman working /w the new version, but in all my linux (un)knowledge I have not been able to do it.  So, I added the edgy repository back to my sources.list file:
```
deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
```

Search for lirc, then highlight it and FORCE the version ( synaptic -> package -> force version ). to 0.8.0-5ubuntu-1

Hope this helps.  

P.S. Does anyone know how to force a .deb version using apt-get or dpkg?  I've tried, but never been successful.  Also, I know how to PIN it, but I really don't want to.

---

### Post by racmar on 2007-07-12
well, I figured out I could pin the lirc package, so along with the additions above:  make a file /etc/apt/preferences and add this:

```

sudo nano /etc/apt/preferences

```

then copy and paste this:

```

Package: *
Pin: release a=feisty
Pin-Priority: 650

Package: lirc
Pin: version 0.8.0*
Pin-Priority: 1001

```

---


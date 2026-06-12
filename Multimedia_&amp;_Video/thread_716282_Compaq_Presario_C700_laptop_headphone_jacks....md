---
title: "Compaq Presario C700 laptop headphone jacks..."
date: 2008-03-05
forum: Multimedia &amp; Video
---

### Post by Grimhound on 2008-03-05
How do I configure things with my Compaq Presario C700 laptop so that the speakers are muted when I have headphones plugged in rather than the sound being routed through both at the same time?

---

### Post by miriad on 2008-03-07
You need to compile and install ALSA 1.15 or 1.16 (Source available from ALSA website).
run the following in terminal:
```

sudo apt-get install build-essential

```
then go to ALSA website, download alsa-driver, alsa-util, alsa-lib, and extract

go into each folder in terminal (in the order listed above), and run the following commands
```

./configure
make
sudo make install

```

Then reboot. the new ALSA HDA-INTEL driver should fix the problem.

---


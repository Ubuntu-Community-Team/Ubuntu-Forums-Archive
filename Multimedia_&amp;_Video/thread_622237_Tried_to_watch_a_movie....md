---
title: "Tried to watch a movie..."
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by GapDragon on 2007-11-24
I attempted to watch a DVD on my brand new Gutsy installation, but Totem Movie Player is telling me it doesn't have the necessary codec(s) to do the job.

This definitely works in Windows (same computer), so how do I update my codec collection so I can watch The Last Mimzy???



Thanks,
GapD

---

### Post by rsambuca on 2007-11-24
You need to install the libdvdcss2 package.  You need to install the medibuntu repositories first.  Open a terminal (Applications -> Accessories -> Terminal) and then run these commands.  First add the medibuntu software repository to your sources:  ```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```Then add the key:```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```Then install the multimedia codecs:```
sudo apt-get install w32codecs
```

---


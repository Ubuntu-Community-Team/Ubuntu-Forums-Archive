---
title: "vlc won't install?"
date: 2006-12-21
forum: Multimedia &amp; Video
---

### Post by doucheone on 2006-12-21
I installed an older version of ubuntu, and vlc installed fine for me.
Today I just re-installed with the newest edgy version and when I try to install vlc using the add/remove applications it tells me 
"VLC media player cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."
Does anybody know what's up with this?
thanks a lot.

---

### Post by meng on 2006-12-21
Trying using Synaptic Package Manager, or drop to the command line and type
sudo aptitude install vlc. Make sure you have universe repositories enabled.

---

### Post by taurus on 2006-12-21
Try to run it from a terminal and see what happens...

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install vlc
```

---

### Post by doucheone on 2006-12-21
> **taurus said:**
> Try to run it from a terminal and see what happens...

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install vlc
```

sweet, that totally worked.
Thanks muchly

---


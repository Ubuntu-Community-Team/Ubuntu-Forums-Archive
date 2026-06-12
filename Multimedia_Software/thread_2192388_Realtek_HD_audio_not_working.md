---
title: "Realtek HD audio not working"
date: 2013-12-07
forum: Multimedia Software
---

### Post by birch2 on 2013-12-07
I recently installed Realtek HD audio drivers on Ubuntu 13.10 and now I have no sound. In the audio manager i get "dummy output" and alsamixer doesn't work. I would like to know a way of removing or fixing it since Realtek does not tell you how to remove it.

---

### Post by khevenhiler on 2013-12-08
Did you restart your computer? :)

---

### Post by Yellow Pasque on 2013-12-08
If ran 'sudo make install' to install the Realtek drivers, then try going to that directory and running:
```
sudo make uninstall
```

Afterwards, reinstall kernel image to restore original sound modules:
```
sudo apt-get install linux-image-`uname -r`
```

---


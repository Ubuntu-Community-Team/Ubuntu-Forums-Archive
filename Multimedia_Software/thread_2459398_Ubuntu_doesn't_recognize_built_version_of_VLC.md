---
title: "Ubuntu doesn't recognize built version of VLC"
date: 2021-03-17
forum: Multimedia Software
---

### Post by dawoodalbadi on 2021-03-17
Hello Guys
Recently I decided to remove snap store which provides the only updated binary of VLC so I needed a way to get VLC which leads me to use source code of vlc. I configure vlc to be installed in /opt/ directory and install it perfectly running with all its features but there is one problem. To run VLC I need to use /opt/vlc/bin/vlc in terminal and there is no other way to start vlc. I tried to link it with normal usr bin directory but I actually didn't understand what link is. I am really confused and I need a way to make ubuntu know what I installed without install it in usr

---

### Post by deadflowr on 2021-03-17
You don't need the snap store to install snaps.

---

### Post by CelticWarrior on 2021-03-18
And VLC is still in the normal repository -> ```
sudo apt install vlc
```
No need to compile it yourself either.

---


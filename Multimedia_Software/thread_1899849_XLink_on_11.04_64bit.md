---
title: "XLink on 11.04 64bit"
date: 2011-12-24
forum: Multimedia Software
---

### Post by timmy2960 on 2011-12-24
I think it's 11.04
Anyway, I tried getlibs to get everything but every time I try sudo ./kaiengine it just spits out
```
desktop@desktop-GG754AV-ABA-a6150e:~/Desktop/kaiEngine-7.4.18$ sudo ./kaiengine
[sudo] password for desktop: 
./kaiengine: error while loading shared libraries: libwx_gtk2u_richtext-2.8.so.0: wrong ELF class: ELFCLASS64

```I accidentally followed a 32bit tutorial first so what can I do to fix this? Anyone know?

---

### Post by timmy2960 on 2011-12-24
Now I feel terrible because I went back to the 32bit tutorial and removed the package it told me to install and kaiengine fired right up. For anyone else who needs it
```
sudo apt-get remove libwxgtk2.8-0
```

---


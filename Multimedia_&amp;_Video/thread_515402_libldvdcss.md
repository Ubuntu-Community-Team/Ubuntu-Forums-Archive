---
title: "libldvdcss"
date: 2007-08-01
forum: Multimedia &amp; Video
---

### Post by fourthdimension on 2007-08-01
Hey All

I'm trying to play dvd's on my machine, and I know I need to download libdvdcss, but when I try I get this error:

```
myusername:~$ sudo apt-get install libdvdcss
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss has no installation candidate

```

Does anyone know what's happening?
Thanks.

---

### Post by aysiu on 2007-08-01
Paste this command into the terminal: ```
echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install libdvdcss2
```

---

### Post by fredj on 2007-08-01
If you want to install multi-media including DVD playback then look at the sticky post at the 
top of this forum and follow it exactly. It really does work so why bother trying to install bit by
bit when the problem has already been solved.

---

### Post by Brindled on 2007-08-02
here's the link to deb packages that will install if all the dependencies are met.

[http://download.videolan.org/pub/libdvdcss/1.2.9/deb/](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/)

---


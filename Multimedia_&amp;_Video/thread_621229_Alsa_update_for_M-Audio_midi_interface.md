---
title: "Alsa update for M-Audio midi interface"
date: 2007-11-23
forum: Multimedia &amp; Video
---

### Post by Sirven on 2007-11-23
Hi, I would like to know how we can upgrade Alsa drivers to 1.0.15 easily. I need to install
a M-Audio Midi interface 1X1. When I try to install manually
the drivers, It says I can't reach source file kernel from the /usr/src folder. 
Message :

checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

What I need to get is snd-usb-audio working as a module. 
Thanks

UbuntuStudio 7.10

---

### Post by chocolatetoothpaste on 2007-11-24
Run this:
```

sudo apt-get install linux-headers-$(uname -r)

```
then try ./configure again

---

### Post by Drunky on 2007-11-24
I haven't read the entire thread but [here]("http://ubuntuforums.org/showthread.php?t=579548") is another thread about updating ALSA to 1.0.15.

---

### Post by Yellow Pasque on 2007-11-24
If you already have the headers and still get the error, it appears you would need to symbolically link (ln -s) /usr/src/linux to point at the kernel headers folder.

---


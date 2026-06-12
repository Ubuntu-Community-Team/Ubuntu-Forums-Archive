---
title: "Nvidia driver install"
date: 2013-07-06
forum: Multimedia Software
---

### Post by Xceptiona1 on 2013-07-06
I have reloaded for the 5th time today and Im not having much luck. I am attempting to run 13.04 and install nvidia drivers. I have tried the nvidia beta drivers from the website and also tried nvidia-current from the repos. both of those appear to install then after a reboot I get the login and once I login the Unity desktop never shows up, just a background.

---

### Post by Bucky Ball on 2013-07-06
*Thread moved to **Multimedia & Video**.*

Please post in correct category. ;)

---

### Post by Xceptiona1 on 2013-07-06
I just tried again and same thing, I went ahead and tried removing lightdm and installing gnome, the login screen changed, however once I login it still just shows an empty desktop.

---

### Post by fooman on 2013-07-06
did you completely remove the first driver you installed?  try running these 2 commands,  one at a time in a terminal:

```
sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
```

---

### Post by KARNVORbeefRAGE on 2013-07-06
Try loading the mainline kernel from the command line:
[http://linuxg.net/how-to-install-kernel-3-10-on-ubuntu-linux-mint-debian-and-derivates/](http://linuxg.net/how-to-install-kernel-3-10-on-ubuntu-linux-mint-debian-and-derivates/)

(64-bit system)
```
wget -c kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-saucy/linux-headers-3.10.0-031000_3.10.0-031000.201306301935_all.deb
wget -c  kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-saucy/linux-headers-3.10.0-031000-generic_3.10.0-031000.201306301935_amd64.deb
wget -c  kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-saucy/linux-image-3.10.0-031000-generic_3.10.0-031000.201306301935_amd64.deb
```

(32-bit system)
```
wget -c kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-saucy/linux-headers-3.10.0-031000_3.10.0-031000.201306301935_all.deb
wget -c  kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-saucy/linux-headers-3.10.0-031000-generic_3.10.0-031000.201306301935_i386.deb
wget -c  kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-saucy/linux-image-3.10.0-031000-generic_3.10.0-031000.201306301935_i386.deb
```

(For both)
```
sudo dpkg -i *.deb
```

---

### Post by BreezyBrooke on 2013-07-06
None bothered to ask the obvious question? What is your graphics card?

---

### Post by Bashing-om on 2013-07-06
And;
Is a driver installed ?
Terminal codes:
To see your graphics card and info:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```

[INDENT][INDENT][/INDENT][/INDENT]And we will see what is to be seen

---


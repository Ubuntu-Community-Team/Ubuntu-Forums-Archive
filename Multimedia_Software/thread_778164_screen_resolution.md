---
title: "screen resolution"
date: 2008-05-01
forum: Multimedia Software
---

### Post by thischarmingman on 2008-05-01
Hi
After accidentally installing the wrong driver using envy I am now unable to change my screen resolution to anything higher than 640X480. The envy driver is installed but it hasn't changed anything. Currently using 8.04 hardy heron LTS, ibm thinkpad t40, radeon 7500. Help will be much appreciated!

---

### Post by Zorael on 2008-05-02
Have you asked envy to remove the driver, to get it properly out of your system? (pun)

To reset your X configuration, enter the following commands. The graphical environment will then start with the default vesa driver, at which point you're back to square one, whereupon you can try a different approach. It'll make a backup of the file, too.
```
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup0805
$ sudo dpkg-reconfigure xserver-xorg
```
It'll ask some questions, then it's done. Save your work, then restart X with Ctrl+Alt+Backspace.

---

### Post by angry_johnnie on 2008-05-02
Zorael is right, but i think that should be

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Zorael on 2008-05-02
Er, yes, thanks. I suck. :<

---

### Post by thischarmingman on 2008-05-02
Thanks guys!

---


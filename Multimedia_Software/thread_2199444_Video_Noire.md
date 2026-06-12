---
title: "Video Noire"
date: 2014-01-13
forum: Multimedia Software
---

### Post by jhsjues on 2014-01-13
Hello,   After upgrading to Ubuntu 13.10, the screen is black at login. Your help is appreciated.  Gracias.

---

### Post by papibe on 2014-01-13
Hi jhsjues.

Press Ctrl+Alt+F1 to get into text mode. There login using your username and password.

There I would try this:
```
sudo mv -iv /etc/X11/xorg.conf  /etc/X11/xorg.conf.old
```
Then restart your computer:
```
sudo reboot
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by jhsjues on 2014-01-14
Gracias for the reply. Moving xorg.conf did not fix the problem. I'm not actually certain what the problem really is, though it's likely a video problem.

---

### Post by papibe on 2014-01-14
If you could ssh into the machine, it would very valuable to see the X log, and the result of some commands.

If you could, please post the results of these commands?
```
lspci -nnk | grep -iA2 vga

lsmod | grep -iE 'nvidia|fglrx|radeon|nouveau|i9'

xrandr -q 

xrandr -q --q1

```
Also, if you could paste this file:
```
/etc/X11/xorg.conf
```
here: [paste.ubuntu.com]("http://paste.ubuntu.com/") and post the link to it.

Regards.

---


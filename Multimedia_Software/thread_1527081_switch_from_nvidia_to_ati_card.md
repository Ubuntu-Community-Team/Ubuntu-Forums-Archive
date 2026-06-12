---
title: "switch from nvidia to ati card"
date: 2010-07-08
forum: Multimedia Software
---

### Post by canabal on 2010-07-08
Hey all,

I just purchased a new ati graphics card as my nvidia is aging and I figured it may help performance.

The issue I am having is it is not creating a new xorg.conf (I need to as I have a dual monitor setup).  I have tried a few things:

1) leaving old xorg.conf and booting into it.  It gives the error about it failing to boot because the nvidia modules.
2) renaming xorg.conf.  It boots into ubuntu fine, but there is still no xorg.conf to configure.
3) I have tried not starting my session on login and going into a console (ctrl-alt-f1) and running sudo Xorg -configure.  It just sits there (I have left it for up to 15 minutes) and no new xorg.conf is created (or xorg.conf.new)
4) I have tried running sudo dpkg-reconfigure xserver-xorg which does nothing

Any thoughts?

---

### Post by arsenic23 on 2010-07-08
Just checking, but did you uninstall the nvidia restricted drivers first?

---

### Post by canabal on 2010-07-08
I did uninstall them, but I did it after I switched the card.  Will I need to switch it back in, uninstall and then switch it back out?

---

### Post by arsenic23 on 2010-07-08
I'm not 100% on this but can't you just uninstall the nvidia drivers, delete/rename the old xorg, and the install the fglrx drivers and reboot?  I normally replace my OS whenever I do major hardware changes so I'm not really sure, but that works in my imagination.

---

### Post by canabal on 2010-07-09
I was hoping to use the open source ati drivers (which I keep hearing good things about), and not fglrx, but I will try that, as it needs to work.

---

### Post by canabal on 2010-07-09
So unfortunately that failed.  A new xorg.conf is not created automatically.

When I run "sudo Xorg -configure" it now no longer freezes with just a cursor sitting in the top corner, it instead comes up with an error.

I will post the error shortly if I can, but it is quite long and I cant see a way to copy it.

---

### Post by canabal on 2010-07-09
I just found the log file, but I am unable to find any errors that should stop it from being created.

The log file is attached, but I was forced to zip it as it was too big as a txt file.

If anyone needs more info, please let me know.

---

### Post by canabal on 2010-07-09
Interesting, I just ran it again, but the log is completely different.  Last time I was at the login prompt, and then hit ctrl-alt-f1 and ran it (after stopping gdm).

This time I ran it after logging in, then did the same (ctrl-alt-f1, stop gdm, run sudo Xorg -configure.)

The log is very different, and much shorter.

---

### Post by pme 72 on 2010-07-11
Here is a link to a discussion on switching from an Nvidia card to an ATI in 8.04:

[http://ubuntuforums.org/showthread.php?t=1373813](http://ubuntuforums.org/showthread.php?t=1373813)

I have no experience with the switch though.

---

### Post by Yellow Pasque on 2010-07-12
I would try this to reset everything: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---


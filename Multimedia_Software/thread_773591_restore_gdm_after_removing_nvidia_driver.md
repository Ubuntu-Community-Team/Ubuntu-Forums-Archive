---
title: "restore gdm after removing nvidia driver"
date: 2008-04-29
forum: Multimedia Software
---

### Post by rperrones on 2008-04-29
Hi,

does anybody know how to enable again gdm to automatically start in the boot process, after removing Nividia driver (GForce 7400)? Now, i need to login in terminal and use "startx" command to start GUI. The xorg.conf was change to "nv" but it doesn't work.

Thanks
Ricardo

---

### Post by volkswagner on 2008-04-29
This post has command to reinstall gdm.  It may help.

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by rperrones on 2008-04-30
Hi,

I solve the problem! but was need to reinstall xserver-org-core package. This is not a conventional way to solve, but now it works fine :)

Thanks
Ricardo

---


---
title: "I broke my xserver :("
date: 2011-03-10
forum: Multimedia Software
---

### Post by Radiobuzz on 2011-03-10
Hey there,

I'm using Ubuntu 10.10 64 bit and I was trying to upgrade my Intel drivers to the last version (2.14). I found this site with a repository available:

[https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)

I've added it and installed the drivers. Everything went well, I mean no error was produced while the drivers were being installed. Problem is, Ubuntu boots but I get no GUI. I get nothing, in fact. I can press ctrl+alt+f1 and such and I get a command line but xserver is just absolutely black.

What can I do?

Thanks!

EDIT: Nevermind, I fixed it. All I did was booting with "nomodeset" and from the console I ran apt-get upgrade, some packages were installed and now everything's back :).

---


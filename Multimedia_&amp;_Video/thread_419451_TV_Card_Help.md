---
title: "TV Card Help"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by ChildOTK on 2007-04-23
Hi all,

I have just this morning loaded up Ubuntu 6.06, and firstly I want to say what a wonderful distro of linux, this has been the easiest one for me to work with out of all the distros I have used.

Anyway, back to the point, I am trying to install my TV Card to get MythTV working, it is a Conexant CX23881-39 PCI Card. Has anybody installed this one before? Or can anybody please offer some help?

I am at present upgrading the Ubuntu packages to the latest.

Any help will be greatly appreciated, thank you.

---

### Post by josesanders on 2007-04-24
Your card uses an saa7134 chipset, so it may not be easy.  First, try to get the card installed correctly.  When you put the card in and start up your machine, run the command:

$ dmesg

If you see errors relating to the saa7134 card, then follow this howto:

[http://ubuntuforums.org/showthread.php?t=408654](http://ubuntuforums.org/showthread.php?t=408654)

Unfortunately, even when you have the card installed correctly, MythTV is an entirely different problem.

---

### Post by ChildOTK on 2007-04-24
Thanks for the reply.

There is nothing about the SAA7134, but there is mention about CX2388x. So it is seeing the card.

Mythtv I am not worried about at present, I would just like to get the actual TV card working.

---

### Post by josesanders on 2007-04-24
Try the card with TVTime.  If you don't already have it installed, run:

$ sudo apt-get install tvtime

After it installs, run the application, and see if you get TV and can change channels.

---


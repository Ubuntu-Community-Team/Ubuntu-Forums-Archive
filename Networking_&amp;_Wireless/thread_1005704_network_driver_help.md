---
title: "network driver help"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by csogilvie on 2008-12-08
I have Ubuntu 8.04 64-bit Desktop installed on a home machine that I mostly use as a light duty web-server.

It has an Asus P5Q motherboard, and sadly 8.04 requires that I recompile and re-install my network driver at each boot... Once I do, it works fine for my purposes. (I'm not interested in upgrading to ibex just yet... I tried and gnome exploded... I'll wait another month before I try again)

I need to do a make, an make install, then an insmod to get the network driver going.

How do I put this into the startup scripts so if I ever need to restart it remotely, I'll be able to log back in once it comes back up?

Cheers.

---

### Post by csogilvie on 2009-02-06
problem solved - 8.10 upgrade.  Kernel includes all the drivers I need.

---


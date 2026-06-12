---
title: "Bluetooth BlueZ stack configuration"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by naren_81a on 2010-12-01
After BlueZ configuration my Desktop is not going into Graphical mode when i restart the Desktop. The following are the packages i have installed on Ubuntu 9.10.

BlueZ-4.81
Glib-2.16.6
openObex-1.5
Obexd-0.37
libdbus-dev from repository.

I tried to reinstall ubuntu 9.10 and 10.04. still i see the same problem. Can some one please help this problem.

---

### Post by outskut on 2011-03-03
Sorry, I don't have a quick solution, and I probably won't be able to stick with the thread right now, but this sounds like a really strange problem.  My guess is that you unintentionally uninstalled or overwrote a library being used by your windows manager/GUI.  I actually had to install several of the same libraries when I was configuring my bluez development environment some time ago.  I found the libraries online, and there was a significant risk of installing one that was dramatically out of date.  Good luck with that, but your reinstallation is the thing that doesn't make sense.  You really need to backup your data and install a new copy of the OS from disk or USB or something to be reliable.  With that done, if you can't boot properly you have a hardware issue, and your bluez installation has nothing to do with it.
-Outskut
P.S.  Use the beginners forum for something like this.

---


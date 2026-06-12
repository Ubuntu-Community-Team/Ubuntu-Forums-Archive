---
title: "ipod nano 3g with banshee"
date: 2010-02-21
forum: Multimedia Software
---

### Post by 80aless on 2010-02-21
Hi,
after upgrading to Ubuntu 9.10 banshee does not see my Ipod anymore, which is a nano video 3g one. Rhythmbox works though, gtkpod not. I thought I had to install libgpod-dev and libgpod2, but the second library is not available anymore in synaptic. I have installed libgpod4, libgpod-common, -dev. 
thanks

---

### Post by boombox1387 on 2010-02-22
This was an issue with the version of Banshee that shipped with Karmic.  This problem should be fixed in the latest release of Banshee (1.5.3).  You can get this release by adding [the Banshee Team PPA]("https://launchpad.net/~banshee-team/+archive/ppa") to your software sources.  After you've added the PPA, just check for updates like normal, and Update Manager should offer to update Banshee.

With any luck, this should make your iPod work again with Banshee.  Without any luck, you may need to run 'podsleuth --rescan' in a terminal while your iPod is mounted and Banshee 1.5.3 is running.  This should be a one-time operation that detects your iPod.

---

### Post by 80aless on 2010-02-22
Thank you very much, it worked!

---

### Post by boombox1387 on 2010-02-22
> **80aless said:**
> Thank you very much, it worked!

Glad to hear it!

---


---
title: "Can't get sound to work...."
date: 2009-07-26
forum: Multimedia Software
---

### Post by computer4u on 2009-07-26
I just can't get the sound to work on my computer. I am a noob to ubuntu, on the 9.04 version, and at first the sound did not work. I tried everything in the stickied topic on the top of this forum section, and none of it worked. I tried reinstalling the sound codecs and everything, tried to get the driver from alsa, but no sucess. When i try to compile my own drivers, this is what happens:
sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
Package linux-headers-2.6.27-14-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.27-14-generic has no installation candidatel

please help me, i may just be doing something easy wrong.

---

### Post by igorzwx on 2009-07-26
aplay -l

---

### Post by Yellow Pasque on 2009-07-26
I'm guessing you upgraded from Ubuntu 8.10, because you're still using a kernel from that distro.

Also, if you're going to compile ALSA from source: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---


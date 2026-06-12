---
title: "How can I create a directory before LIRC starts?"
date: 2010-02-04
forum: Multimedia Software
---

### Post by ffonz on 2010-02-04
Not many people read my previous item ([http://ubuntuforums.org/showthread.php?t=1396967](http://ubuntuforums.org/showthread.php?t=1396967)). I guess my title wasn't good.

After reading my previous item, can someone answer the following questions:
Has anybody have an idea why my lirc directory is removed after every reboot? Or how can I create this dir before lirc is started?

---

### Post by lloyd_b on 2010-02-04
> **ffonz said:**
> Not many people read my previous item ([http://ubuntuforums.org/showthread.php?t=1396967](http://ubuntuforums.org/showthread.php?t=1396967)). I guess my title wasn't good.

After reading my previous item, can someone answer the following questions:
Has anybody have an idea why my lirc directory is removed after every reboot? Or how can I create this dir before lirc is started?

The answer to why it's being removed is simple - '/var/run' is NOT an "real" directory.  Instead, it's the mount point for a virtual filesystem that's created by the kernel at each reboot, and exists only in memory.

There may be a "better" way to do this, but for now just edit the file "/etc/rc.local", and add "mkdir /var/run/lirc" somewhere before the "exit 0" line.  This will recreate the directory at every boot (you don't need a 'sudo' on this, as that script always runs as root).

Note that you'll need root permissions to change that file, so "sudo nano /etc/rc.local" in a terminal window or something equivalent.

Lloyd B.

---

### Post by ffonz on 2010-02-10
Thanks lloyd, that did the trick!

---


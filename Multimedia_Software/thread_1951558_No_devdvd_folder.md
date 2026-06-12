---
title: "No /dev/dvd folder?"
date: 2012-04-02
forum: Multimedia Software
---

### Post by drgears882 on 2012-04-02
Forgive me, I'm still somewhat new to Ubuntu, and am still feeling my way about.

On a earlier distribution, 10.something-or-other, i was able to play DVDs without incident after installing the various restricted directories and libraries.  However, since upgrading to 11.10, i've been unable to play any DVD movies.  Games and music CDs seem to come up fine, however movies either do not show up at all, or appear as a blank disk.

After flailing about and re-installing the various directories, I attempted to see if the system could at least SEE the drive.  Following various advice, I sought out the "/dev/dvd" folder, only to find that it doesn't exist.  The only thing that appears even similar is "/dev/disk", but i don't think it's the same thing.

I'm at a general loss, as I think I know just enough to SEE the issue, but not actually FIX it.  Again, forgive me if this is a simple, easy fix, but i would greatly appreciate any help that could be offered.  Thank you so much in advance.

---

### Post by akaihola on 2012-04-21
You might have to modify /etc/udev/rules.d/70-persistent-cd.rules to correct the symlinks created by udev. Search Ask Ubuntu for detailed instructions (try "/dev/dvd" as search terms). After editing the file, you can make the changes take effect without rebooting by typing "sudo udevadm trigger".

---

### Post by drgears882 on 2012-04-21
Humm...i've tried that, and it looks like a bunch of drivers from my android phone got installed to that file, and are clogging it up.  The issue is, i can't make any changes to it.  Even enabling root access in the terminal and trying to access the file that way tells me I don't have access.  Any suggestions?  Again, sorry if i'm a little unclear with this, and i'm more then happy to follow any directions given.  Thanks for at the very least checking in to this!

---


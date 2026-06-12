---
title: "Sound totally gone in 8.04"
date: 2008-06-28
forum: Multimedia Software
---

### Post by tonu on 2008-06-28
Upgraded to 8.04 from 7.10 and all seams to be OK.

Then did an update (can't remember which) and ALL sound gone - no Login, no start-up theme, nothing but Youtube and other videos still run silently!

Have a swappable HD rack system.

Took the HD, with 8.04, out and inserted the HD with Win Xp and ALL sound OK!

Tried my third (old 40GB) HD with PCLinuxOS and all OK!

Left Rack slot empty and tried "Live DVDs" - Knoppix, PCLinuxOS and 7.10 - all had sound!

What gives?

Thinking of formatting the "/" partition and reinstalling 8.04 but not sure if all files on "/Home" will be safe?

Tõnu Soovere
Toronto, ON Canada

---

### Post by ouchouchouch on 2008-06-28
Your /home will not be safe for certain unless it is on another disk, like this.

ben@mallory:~$ df -h / /home
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             133G  3.1G  124G   3% /
/dev/sde1             459G   48G  389G  11% /home

If your /home is another partition on the boot disk, then it will not get stepped on unless you select "guided use entire disk" or partition it manually and make a mistake stepping on your /home. If your /home is part of the same physical file system as / you must back it up and test the backup before you do anything to it.

I just re-installed / to fix a sound problem. I had /home on a separate disk and it was easy to set things back to how they were.

---

### Post by tonu on 2008-06-29
Thanks, my system is partitioned :

tonu@tonu-desktop:~$ df -h / /home
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  4.0G  7.3G  36% /
/dev/sda3              60G  3.5G   54G   7% /home


So, now I download and burn a new .ISO disk of 8.04 and run it?

How did you re-install just the "/" partition?

What happens to my Firefox 3 Bookmarks?

Have read that some have reverted to Firefox 2 as if Firefox 3 is the problem?

What is the problem, does anyone know?

---


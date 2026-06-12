---
title: "Mythbuntu 9.10, MythTV 0.22 and mtd"
date: 2009-11-21
forum: Mythbuntu
---

### Post by drumz on 2009-11-21
I have a standalone front end box running Mythbuntu 9.10 (MythTV 0.22) that I for streaming video from a server (Ubuntu 9.10 system that has MythTV 0.22).  I've also used this front end box to replace the DVD player which is where my problem is coming up.

If I boot the system without a DVD in the drive, about 490MB of memory is used out of the 2GB I have installed.  Immediately after putting a DVD in the drive, almost all of the memory is used (only 70K is left free) and it starts swapping.  DVD playback stutters periodically during playback.

Digging further, it's the 'mtd' process that doing it - it's causing 49% I/O wait on the system because of the swapping and uses over 2.1GB of memory.  This only happens when a DVD is in the drive.  Ejecting the DVD results in the I/O wait dropping to 0% but mtd retains all of the memory it's chewed up.

What's going on with mtd?

---

### Post by drumz on 2009-11-24
Ok, so I increased the amount of memory in the system and installed the 'pae' version of the kernel so it would see it.  This 'solved' the problem albeit by the brute force method of increasing physical memory.

I have a few additional observations:

1.  mtd is started as the box boots, not exactly sure WHY it's started (see below).

2.  If a video DVD is in the drive on boot, mtd chews up the 2.5GB of memory.  If the DVD is put in the drive after everything is booted it seems mtd does NOT chew up memory although it's still running.

3.  Killing the mtd process while a DVD is playing back does not affect playback - memory is immediately freed but no hick-ups appear in playback.

Anyhow, everything is working as I need it to.

---

### Post by pcooley on 2010-01-24
For your edification: I just noticed this too on a similar configuration (Mythbuntu 9.10, MythTV 0.22).


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1988 mythuser   39  19 3707m 3.1g 1948 S    8 85.3   3:10.04 mtd

---

### Post by johnnysako on 2010-04-04
I have also noticed this on my configuration.  Mythbuntu 10.04.  It seems specifically related to some Disney/Pixar DVDs.

---


---
title: "Natty + W7 - On reboot, system hardware crash, needs powering off"
date: 2011-04-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Ju5tP00 on 2011-04-20
Hey all, I've been triple booting happily with Ubuntu 10, XP and W7. I upgraded 10 to Natty 64, and have had a few niggles, with one major problem.     Booting into Ubuntu is fine and quick, quickest yet at about 20 secs, but upon restarting the PC has a serious problem.     I select w7 from the grub menu, it gets to the logon screen and fails, upon rebooting it only reaches the bios screen then fails. The only way to get the pc to even turn on properly is to remove the power until the motherboard has fully powered down. It then boots normally.     I've been unable to reproduce this problem switching from XP to W7, XP to Ubuntu, W7 to Ubuntu, XP to Ubuntu, or simply restarting either of the Windows installations. It only happens when switching from Natty to either of the Windows installations.     I reinstalled Ubuntu 10 and cannot reproduce the problem, upon reinstalling 11 the issue returns.   For the record my hardware is a Dell XPS 630i, q6600, 8800gt SLI with three samsung monitors. The installations are running off a 500gb Seagate partitioned into four, with 2 other drives as storage.     The problem is catastrophic to the system, no hardware works properly until the power is removed completely and reset.  Any advice would be appreciated. For the meantime I think I'll roll back to 10. Thanks, Paul

---

### Post by torgrot on 2011-04-20
That's why they call it beta.

---

### Post by Ju5tP00 on 2011-04-20
Even for a buggy beta, this is an unusual problem - and worth reporting. An OS that stops a PC even posting is beta indeed.

---

### Post by Dutch70 on 2011-04-20
The only thing I can think of that may have something to do with it is that Natty uses grub version 1.99. Maverick uses 1.98. I have several distro's on my computer, and when I get a kernel upgrade for Kubutnu or Ubuntu Natty, there are some systems that don't want to boot until I reinstall grub (version 1.98. to Maverick.

---

### Post by uRock on 2011-04-20
Moved to Natty Narwhal Testing & Discussion.

Have you file a bug report? 

Did you test the image before installing? 

Did you change the bios settings to tell the system to boot from CD/USB? If yes, did you undo this change after installing?

---

### Post by Ju5tP00 on 2011-04-20
Yes the MD5 checked out, I manually selected to boot from CD, no BIOS changes made. I'll file a report now.

The problem appears during the bios, but I'll try the older loader, once I've figured how :)

---

### Post by Ju5tP00 on 2011-04-22
Changed the grub version and the problem remains, so I've gone back to Ubuntu 10 for the meantime. I filed a bug report, I can't see anyone else posting anything similar. It's one hell of a bug, I've never seen anything like it. The fact that it can only be fixed by removing the power and reseting the board would indicate that Natty is changing something at hardware/bios/cmos level - can that be right?

---

### Post by Hedgehog1 on 2011-04-22
> **Ju5tP00 said:**
> Changed the grub version and the problem remains, so I've gone back to Ubuntu 10 for the meantime. I filed a bug report, I can't see anyone else posting anything similar. It's one hell of a bug, I've never seen anything like it. The fact that it can only be fixed by removing the power and reseting the board would indicate that Natty is changing something at hardware/bios/cmos level - can that be right?

I have managed to crash a few Linux servers that bad without my code altering hardware/bios/cmos levels (and did I get yelled at in the process! It only had 100 users on it, after all).

I was seeing a 'never shutting off' on reboot and 'log-off hanging' (as were other testers) that appears to be fixed after Thursdays updates (I loaded them on Thursday my time, they may have been Wednesdays updates). This only happened on the laptop Natty test install, the desktop running an identical Natty test install did not exhibit the error.

My 'trusted' OS is still 10.10, but Natty has made serious leaps and bounds in the last few days.

***The Hedge***

:KS

---


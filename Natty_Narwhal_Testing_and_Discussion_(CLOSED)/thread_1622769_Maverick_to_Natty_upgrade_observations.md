---
title: "Maverick to Natty upgrade observations"
date: 2010-11-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Aide9aic on 2010-11-15
(...My first post here...been self-learning Linux and Ubuntu for about six months now, fun fun...)

Did the upgrade twice. Formatted disk, installed Maverick, followed the procedures documented in the forum for using aptitude with safe-upgrade etc. Some things to report:

* First time I put /boot on an EXT4 partition and / on a BTRFS partition. Mount options in FSTAB included noatime,nobarrier,nodatacow. The safe-upgrade took 90 minutes to install.

* Second time I used EXT4 for both partitions, set noatime in FSTAB, and used tune2fs to disable journaling. This time, safe-upgrade completed in 15 minutes. Wow, what a difference! Is BTRFS really still so broken?

* Alt+F2 for run programs isn't working and CTRL+ALT+T won't bring up a terminal window.

* Had to install gnome-panel-bonobo to get indicators working.

* Whenever I try a shutdown, a dialog informs me that Window Manager is unresponsive.

Otherwise, things look good so far. Before I did the upgrade I removed stuff I don't use: OpenOffice, Firefox (I'm happy with Ephiphany), Asian fonts, games. Today's safe-upgrade politely informed me these packages are recommended but won't be installed. Nice.

---

### Post by cariboo on 2010-11-16
It's pretty early in the testing cycle, we're still at the pre-alpha stage, Don't worry though, there is still lots of breakage to come. :)

You may want to join in the fun of testing Unity. Have a look [here]("https://wiki.ubuntu.com/Unity/InstallationGuide").

---

### Post by Aide9aic on 2010-11-16
Sure, I'm not expecting everything to be perfect. I wasn't much of a fan of Unity when I first saw it in Maverick netbook, has it changed much? I'll check it out.

Meanwhile, I'm very curious about the wild speed differences in EXT4 vs BTRFS. I've seen some of the various benchmarks (including the stuff on Phronix -- combative folks in the comment threads there). I was shocked at how terribly BTRFS performed during my upgrade as compared to EXT4.

---

### Post by cariboo on 2010-11-16
> **steveriley said:**
> Sure, I'm not expecting everything to be perfect. I wasn't much of a fan of Unity when I first saw it in Maverick netbook, has it changed much? I'll check it out.

Meanwhile, I'm very curious about the wild speed differences in EXT4 vs BTRFS. I've seen some of the various benchmarks (including the stuff on Phronix -- combative folks in the comment threads there). I was shocked at how terribly BTRFS performed during my upgrade as compared to EXT4.

I'd suggest you check out the Unity mega thread to see what is happening with Unity.

I found BTRFS to be much slower that ext4, when i tried it last month. As far as I'm concerned, it isn't ready for prime time yet,

---


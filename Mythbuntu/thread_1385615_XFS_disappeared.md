---
title: "XFS disappeared?"
date: 2010-01-19
forum: Mythbuntu
---

### Post by dougsnell on 2010-01-19
I recently moved to a new (larger) hard drive, and based on the suggestions moved from ext3 to xfs.  I had an issue where the hard drives were getting mixed up - following the instructions I found ([http://ubuntuforums.org/archive/index.php/t-596433.html](http://ubuntuforums.org/archive/index.php/t-596433.html)), I was getting bounced into grub, and forced to manually edit the line from (hd2,0) to (hd0,0) at every boot.  Not a big deal, but tonight I found it stopped at that prompt again, and went in to fix it.

I was trying to diagnose why I kept getting "checking if xfs_stage1_5 exists... no" errors, when I booted to the LiveCD (probably the 5th time tonight) and suddenly I could not mount the hard drive.  Normally I just click Places and the drive ... and it would mount and I could browse.  This time, it wasn't listed.  I went into gParted, and noted the partition was listed as unknown.  I tried fsck (which re-directed me to xfs_something?), and it would still not recognize.

I'm currently running SpinRite on the disk, but I don't really think it's going to fix anything.  I don't recall modifying the partition or type in any fashion.  My guess is it didn't dismount properly during a reboot?  Not important.  Possibly worthwhile, I note the "bootable" flag was not set on the drive.

So,

1.  Is there anything I can attempt to try to force a check on the xfs partition?  If fsck is my only option, I could probably use a spot-check on what I should be typing, just to be sure I'm typing it correctly.
2.  Noting the issues I have read on xfs and power outages, is there any way to convert to another FS, or any suggestions on a better FS type?  I would imagine I could re-size XFS, create ext4, copy everything, and re-size appropriately.

Maybe I just ran into a different problem, and the issues with xfs and power outages have resolutions I'm not aware of?  Regardless, any help is greatly appreciated.

---

### Post by dougsnell on 2010-01-20
Updated info - I did manage to make some progress, but I'm still unable to boot.  I ran testdisk from a LiveCD, and it found (with a deeper search) both partitions, wrote them to the table, and appeared to be OK.

I now get stopped at GRUB, type "boot", and receive "Error 8: Kernel must be loaded before booting".  I ran root (hd0,0) and setup (hd0) ... and as suspected, went nowhere.  Going back into the LiveCD, it still doesn't recognize the drive.  I'm running testdisk again, and do note it recognizes the partitions, but said something about "no ext ... or xfs markers".

I assume either I didn't write something properly, am missing something key on the LiveCD, or the GRUB commands I'm running are destroying what I'm trying to fix ;)  I'll give it another whirl tomorrow AM, but in the meantime, if anyone has any suggestions, I'm all ears.  I figure all my data appears to be intact ... but I can't get to it.

---

### Post by dougsnell on 2010-01-25
Just a quick note for anyone with some morbid curiosity ....

I was unable to recover the XFS ... or, at least I gave up on it.  After having fsck try to repair for over two days, I cut it off and simply rebuilt it.  Sucks to have lost some stuff, but post-rebuild, certain things actually work better.

I re-built with Myth 9.04.  I have a PVR 350 (and a dual-tuner 500), and still the build for 9.10 is not complete to use it.  I've found a number of people struggling with this.  9.04 was set up and running in about 2 hours of intermittent attention.

The only thing I can't figure out is the keystroke I used to skip to the flagged commercial break.  Unfortunately I lost all the config info, and I haven't stumbled onto the utility that captures IR commands.  I assume I'll then have to remap the key to the correct keystroke.

---

